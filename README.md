# 🌍 EcoMonitor — Lista 12: Do Protótipo ao Código

> Projeto desenvolvido para a disciplina **Interação Humano Computador e UX**  
> Centro Universitário UNA — Professor Daniel Henrique Matos de Paiva

---

## 👤 Identificação

- **Nome:** _(seu nome completo aqui)_
- **Curso:** _(seu curso aqui)_

---

## 📖 Sobre o Projeto

O **EcoMonitor** é uma prova de conceito (PoC) para o sistema de gamificação da ONG **ReCiclo**. O painel permite que o usuário registre ações sustentáveis e acompanhe seu impacto acumulado em tempo real, utilizando componentes Blazor Interactive Server.

---

## 🧠 Heurísticas de Nielsen Aplicadas

### 1. Visibilidade do Status do Sistema
O contador de pontos (`Total acumulado`) é atualizado imediatamente após cada clique no botão **Registrar Atividade**, sem nenhum atraso ou navegação extra. A barra de progresso reforça visualmente o avanço do usuário em direção à meta de 100 pontos.

### 2. Feedback e Controle do Usuário (Reconhecimento ao invés de Memorização)
A badge colorida muda de cor progressivamente (azul → verde → dourado) conforme o total cresce, e a mensagem **"🏆 Meta batida! Você é um Herói do Planeta!"** aparece ao atingir 100 pontos. O usuário não precisa memorizar sua situação — o sistema comunica o estado atual de forma clara e imediata.

---

## ⚙️ Guia de Execução

### Pré-requisitos
- [.NET 8 SDK](https://dotnet.microsoft.com/download) instalado

### Passos

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/una-blazor-lista12.git
cd una-blazor-lista12

# 2. Execute o projeto com perfil HTTPS
dotnet run --launch-profile https
```

Acesse em: `https://localhost:5001` (ou a porta indicada no terminal)

---

## 🔧 Explicação Técnica: Uso do `[Parameter]`

O componente `EcoStatus.razor` recebe dois parâmetros externos:

```csharp
[Parameter] public string NomeAcao { get; set; } = "Ação";
[Parameter] public int PesoAcao { get; set; } = 1;
```

Isso permite que o mesmo componente seja reutilizado múltiplas vezes na `Home.razor` com configurações diferentes, sem duplicar código:

```razor
<EcoStatus NomeAcao="Reciclagem de Plástico" PesoAcao="1" />
<EcoStatus NomeAcao="Descarte de Eletrônicos" PesoAcao="5" />
<EcoStatus NomeAcao="Plantio de Árvores"      PesoAcao="10" />
```

Cada instância mantém seu próprio estado interno (`private int Total`), garantindo independência entre os cartões.

---

## ⭐ Desafios Extras Implementados

| Funcionalidade | Descrição |
|---|---|
| **Barra de Progresso** | Preenchida proporcionalmente ao total (máx. 100 pts), com animação CSS |
| **Estilização Condicional** | Badge muda de azul → verde (≥50 pts) → dourado (≥100 pts) |
| **Mensagem de Conquista** | "🏆 Meta batida! Você é um Herói do Planeta!" exibida ao atingir 100 pts |

---

## 📁 Estrutura do Projeto

```
EcoMonitor/
├── Components/
│   ├── Pages/
│   │   └── Home.razor          # Página principal com 3 instâncias do componente
│   ├── EcoStatus.razor         # Componente reutilizável de ação ambiental
│   └── ...
├── README.md
└── ...
```
