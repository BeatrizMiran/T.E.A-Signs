Pessoa com TEA
Permissões
Acessa apenas seus próprios dados
Pode registrar emoções.
Pode ver alertas que o sistema gerou pra ele.

Funcionalidades
Ver estado atual
Registrar humor
Ver histórico de crises
Receber notificação quando sensores detectarem risco

Endpoints
GET /autista/profile
POST/autista/estado-emocional
GET /autista/alertas
GET/autista/historico

Responsável
Permissões
Pode registrar observações sobre crises.
Pode ver tudo do autista vinculado ao seu humor. 

Funcionalidades
Painel com alertas do autista
Lista de crises do mês
Notificações sobre alteração de humor 
Baixar relatório
acesso a paginas de ajuda profissional 

Endpoints
GET /responsavel/autista/{id}/alertas
GET/responsavel/autista/{id}/historico
POST/responsavel/autista/{id}/observacoes

Educador
Permissões
Pode registrar crises durante o horário escolar

Funcionalidades
Registrar um episódio ocorrido em sala
Acompanhar sinais em tempo real durante o período escolar
acesso a paginas de ajuda profissional 

Endpoints
POST/educador/registrar-crise
GET /educador/alertas-ativos

Terapeuta
Permissões
Pode ver histórico completo do autista (se autorizado)
Pode adicionar notas terapêuticas
Pode ver gráficos e padrões

Funcionalidades
Acessar dados analíticos e gráficos
Inserir observações clínicas
Sugerir estratégias

Endpoints
GET /terapeuta/autista/{id}/relatorio
POST/terapeuta/autista/{id}/nota-clinica
GET /terapeuta/autista/{id}/padroes

Registro de Crises
Banco (tabela: crises)
Campos:
id
user_id
tipo
intensidade
descricao
data_hora
foi_pre_sinal (bool)
registrado_por (educador, responsável, sensor)

Endpoints
POST/crises
GET /crises/{id}
GET /autista/{id}/crises

Dispositivos e Sensores
Banco (tabela: dispositivos)
Campos:
id
user_id
tipo_dispositivo
status
ultimo_dado

Endpoints
POST /dispositivos
POST/dispositivos/{id}/dados
GET/dispositivos/{id}

sistema
Quando um sensor envia:
batimento > limite Ou ruído > limite
→ cria alerta automático
→ notifica responsável + educador

Desenvolvedor 
Permissões
Pode tudo.
Gerencia usuários e sensores.
Configura limites de alerta.

Endpoints
GET /admin/usuarios
PATCH dmin/usuario/{id}
POST/admin/config-alertas

SISTEMA DE AUTENTICAÇÃO 
Endpoints
POST/auth/register
cadastra qualquer tipo de usuário

POST/auth/login
retorna JWT

POST/auth/logout

GETauth/me
retorna dados do usuário logado pelo token
