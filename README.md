# AZELF
Plataforma inteligente de aprendizagem, projetos digitais e desenvolvimento de habilidades.

## Arquitetura
- Frontend: React + Vite
- Hosting: Cloudflare Pages
- Backend: Supabase Auth, PostgreSQL, RLS e Edge Functions
- Tutor: função Supabase `ai-tutor`, que chama OpenAI no servidor
- PWA: instalável em navegadores compatíveis (iOS, Android e desktop)

## Desenvolvimento
```bash
npm install
npm run dev
npm run build
```

## Cloudflare Pages
- Projeto: `azelfone`
- Framework: Vite
- Build command: `npm run build`
- Output directory: `dist`
- Node.js: 22

Variáveis públicas de build:
- `VITE_SUPABASE_URL`: URL do projeto Supabase
- `VITE_SUPABASE_ANON_KEY`: chave publishable/anon do projeto

A chave publishable/anon é destinada ao cliente e só deve ser usada com RLS revisado. Nunca colocar `service_role`, `SUPABASE_SECRET_KEYS` ou `OPENAI_API_KEY` no bundle, GitHub, variáveis VITE_ ou código do navegador.

## Integrações Supabase já utilizadas
- Tabelas: profiles, user_roles, activation_codes, courses, lessons, tools, lesson_progress, ai_conversations, ai_messages e ai_usage.
- Edge Functions: `activate-account`, `admin-manage`, `admin-codes` e `ai-tutor`.
- O tutor recebe o contexto da trilha/aula e do diagnóstico, respeitando o contrato da função de backend.
- Códigos de ativação são vinculados ao e-mail do usuário.

## Funcionalidades implementadas nesta base
- Landing page responsiva
- Cadastro com código de ativação e login
- Diagnóstico de objetivos, áreas, ferramentas conhecidas, atividade atual, tempo disponível, meta de seis meses e visão de futuro
- Catálogo de cursos, aulas e ferramentas carregados do Supabase
- Registro de progresso por aula
- Tutor IA flutuante contextual
- Painel administrativo com visão geral, gestão de usuários e códigos de ativação
- Restrição de conteúdos marcados como exclusivos para adultos
- Fluxo pendente para contas declaradas como menores, com e-mail do responsável e registro manual de verificação pelo administrador
- Manifest, ícone e service worker PWA

## Limites e pendências antes de lançamento público
1. O fluxo de confirmação do responsável nesta versão exige validação manual pelo administrador; não existe confirmação automática por e-mail nem verificação documental.
2. Validar RLS, grants e Edge Functions com contas reais de aluno, menor e administrador.
3. Completar edição/publicação de cursos, aulas, ferramentas e posts no painel.
4. Implementar termos, política de privacidade, retenção e solicitações de exclusão/portabilidade.
5. Testar instalação PWA em iOS e Android reais, acessibilidade, performance e recuperação de senha.
6. Validar limites de IA, custos e tratamento de dados antes de abrir cadastro público.
7. Rever textos e conteúdo didático com especialistas; cursos de trading/cripto são educacionais e não fornecem sinais ou recomendação personalizada.

O projeto não promete ganhos, emprego ou rentabilidade.
