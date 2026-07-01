# Sistema de Gestão para Clínica Médica - Mais Saúde

[cite_start]Este repositório contém o desenvolvimento do **Sistema de Gestão para a Clínica Médica - Mais Saúde**, cujo objetivo é informatizar, centralizar e otimizar os processos administrativos e clínicos da instituição[cite: 7, 19]. [cite_start]A plataforma engloba uma aplicação web dedicada à operação interna e um aplicativo móvel voltado para a experiência do paciente[cite: 20].

---

## 📌 Visão Geral do Projeto
[cite_start]O sistema foi projetado para eliminar o uso de documentos físicos e otimizar o tempo de atendimento por meio de uma plataforma segura, integrada e auditável[cite: 21, 28]. [cite_start]Entre os benefícios esperados estão a redução de erros manuais, maior controle de prontuários, garantia de integridade dos dados e capacidade de atendimento remoto[cite: 22, 27].

---

## 👥 Atores do Sistema (Perfis de Acesso)
[cite_start]O controle de acesso é baseado em papéis (**RBAC - Role-Based Access Control**), dividindo-se em cinco perfis distintos[cite: 13, 147]:
* [cite_start]**Administrador:** Responsável pelo gerenciamento estratégico, configurações de TI e controle total de usuários e permissões[cite: 31, 126].
* [cite_start]**Médico:** Profissional que realiza os atendimentos clínicos, gerencia sua própria agenda, acessa históricos médicos e emite prescrições digitais[cite: 30, 118, 123].
* [cite_start]**Recepcionista / Secretária:** Operador do balcão de atendimento físico, responsável pelo fluxo de agendamentos, atualizações de status e faturamento[cite: 29, 109, 115].
* [cite_start]**Paciente:** Usuário final que utiliza o portal ou aplicativo móvel para se cadastrar, consultar horários, agendar/cancelar consultas e teleconsultas[cite: 32, 33, 102].
* [cite_start]**Farmacêutico:** Responsável por gerenciar o estoque, atualizar a disponibilidade de medicamentos na plataforma e registrar as dispensações[cite: 34, 35, 137].

---

## 🔍 Escopo Funcional (Módulos)

[cite_start]O sistema é composto por 6 macro-módulos funcionais[cite: 37, 65]:

### 1. Módulo de Pacientes
* [cite_start]Autocadastro de pacientes via web/mobile e validação de documentos[cite: 38].
* [cite_start]Manutenção de dados cadastrais (CRUD) por níveis de acesso autorizados[cite: 11, 39].
* [cite_start]Busca indexada de pacientes utilizando filtros por **Nome Completo** ou **CPF**[cite: 40].
* [cite_start]Exclusão lógica de cadastros em estrita conformidade com a **LGPD**[cite: 42].

### 2. Módulo de Profissionais e Equipe
* [cite_start]Cadastro e categorização de colaboradores de acordo com suas funções técnicas[cite: 43].
* [cite_start]Gerenciamento e atualização de dados de médicos e equipe de apoio com histórico imutável[cite: 45, 46].

### 3. Módulo de Especialidades e Planos de Saúde
* [cite_start]Cadastro de operadoras de saúde conveniadas[cite: 49].
* [cite_start]Vínculo dinâmico entre profissionais cadastrados e os planos atendidos[cite: 50].

### 4. Módulo de Agendas e Consultas
* [cite_start]Agendamento de consultas presenciais ou online com validação automática de grades e horários[cite: 51].
* [cite_start]Cancelamento em tempo real com liberação imediata do horário na agenda médica[cite: 52].
* [cite_start]Visualização da agenda em formatos diário, semanal ou mensal[cite: 53].
* [cite_start]Atualização de estados do fluxo de atendimento (*Agendada, Aguardando Atendimento, Em Atendimento, Realizada ou Cancelada*)[cite: 54].
* [cite_start]Disparo automatizado de notificações e lembretes via e-mail, SMS ou *Push Notifications* na véspera do agendamento[cite: 55].

### 5. Módulo Clínico, Prontuário e Telemedicina
* [cite_start]**Prontuário Eletrônico do Paciente (PEP):** Registro estruturado contendo anamnese, evolução clínica e hipóteses diagnósticas[cite: 57].
* [cite_start]**Integração CID-10:** Sistema de busca indexada para codificação internacional de doenças[cite: 57].
* [cite_start]**Sala Virtual de Telemedicina:** Infraestrutura integrada de videoconferência criptografada em tempo real para consultas remotas[cite: 60, 83].
* [cite_start]Consulta unificada ao histórico clínico retroativo do paciente[cite: 58].

### 6. Módulo de Medicamentos e Prescrições
* [cite_start]Cadastro de medicamentos com especificação de princípio ativo, dosagem e nome comercial[cite: 61].
* [cite_start]Controle de estoque e atualização de status de disponibilidade (*Disponível / Indisponível*) gerenciado exclusivamente pelo farmacêutico[cite: 62, 137].
* [cite_start]Emissão de receita digital vinculada diretamente ao atendimento do PEP, emitindo alertas em caso de indisponibilidade de insumos[cite: 63].
* [cite_start]Rastreabilidade de dispensação e retirada de medicamentos através do CPF do paciente[cite: 64, 101].

---

## 🔒 Regras de Negócio Cruciais (RN)
[cite_start]Para garantir a consistência e a segurança jurídica das operações médicas, as seguintes regras foram estabelecidas no núcleo do sistema[cite: 28, 157]:
1.  [cite_start]**Unicidade Cadastral:** É mandatória a validação de CPF único para pacientes e CRM único e regularizado para médicos[cite: 84, 85].
2.  [cite_start]**Prevenção de Concorrência:** O sistema bloqueia estritamente o agendamento duplo de duas consultas para o mesmo médico no mesmo dia e horário[cite: 87, 146].
3.  [cite_start]**Segurança do Prontuário:** O registro de informações no PEP só é liberado após a abertura formal do atendimento e a realização da consulta[cite: 88, 146].
4.  [cite_start]**Imutabilidade Clínica:** O histórico médico e os logs de prontuários nunca são excluídos fisicamente, garantindo a rastreabilidade legal exigida pelo CFM[cite: 94, 148].
5.  [cite_start]**Restrição de Prescrição:** Apenas médicos autenticados e ativos podem assinar receitas digitais[cite: 92].

---

## ⚡ Requisitos Não Funcionais Relevantes (RNF)
* [cite_start]**Desempenho:** Tempo de resposta inferior a 3 segundos para consultas simples e menor que 5 segundos para processamentos complexos[cite: 69].
* [cite_start]**Disponibilidade:** Mínima de 99,5% durante o horário de funcionamento operacional da clínica[cite: 71].
* [cite_start]**Segurança:** Criptografia fim a fim nas teleconsultas, encerramento automático de sessões inativas e logs de auditoria imutáveis para operações de `INSERT`, `UPDATE` e `DELETE`[cite: 73, 74, 83, 157].
* [cite_start]**Compatibilidade & Acessibilidade:** Interface web responsiva compatível com Chrome, Edge e Firefox; aplicativos nativos ou híbridos para Android e iOS; conformidade com as diretrizes de acessibilidade **WCAG**[cite: 77, 78, 81].
* [cite_start]**Resiliência:** Rotinas automatizadas de backup diário com planos validados de recuperação de desastres[cite: 75, 76].

---

CREATE TABLE logs_auditoria (
    id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT NOT NULL,
    acao ENUM('INSERT', 'UPDATE', 'DELETE') NOT NULL,
    tabela_afetada VARCHAR(50) NOT NULL,
    registro_id INT NOT NULL,
    dados_antigos JSON NULL,
    dados_novos JSON NULL,
    data_hora TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

 Equipe de Desenvolvimento do Projeto
- Yosef Klinsman – Gerente de Projeto  
- Letícia Salvador – Gerente de Configuração / Analista de Negócios
- Marcelo Aguiar – Arquiteto de Software / Engenheiro de Qualidade   

## 🛠️ Sugestão de Arquitetura Técnica (Para o Repositório)

```plaintext
├── .github/             # Workflows de CI/CD
├── src/
│   ├── backend/         # API em Java / Python (com logs de auditoria robustos)
│   ├── frontend-web/    # Painel Administrativo, Médico e Recepção (Web responsivo)
│   └── mobile/          # Aplicativo do Paciente (Android/iOS)
├── database/            # Scripts SQL e migrações do banco de dados relacional
└── docs/                # Diagramas UML (Casos de Uso, Atividades, Sequência e Classes)



link trello: [https://trello.com/b/oGGo1Cjz/projeto-clinica-medica]
