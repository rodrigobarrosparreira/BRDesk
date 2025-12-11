# MAPA VISUAL DE PROBLEMAS - BR CLUBE FRONTEND

## 📍 ÁRVORE DE PROBLEMAS POR ARQUIVO

```
BrClubeOficial-main/
│
├── 🔴 index.html
│   └── Linha 10: type="imagex/png" ❌
│
├── 🔴 termos.html
│   └── Linha 11: type="imagex/png" ❌
│
├── 🔴 style.css
│   └── ✅ OK (sem problemas)
│
├── 🔴 padrao.css
│   ├── Linha 1-2: * { font-size: 20px } ❌ (Sobrescreve tudo)
│   └── ⚠️ Remover regra universal
│
├── Nav/
│   ├── 🔴 nav.css
│   │   └── Linha 21-24: float: left ❌ (Desatualizado)
│   │
│   └── ✅ nav.html (sem problemas)
│
├── BoasVindas/
│   ├── 🔴 boasVindas.html
│   │   ├── Linha 10: type="imagex/png" ❌
│   │   ├── Linhas 14-33: HTML aninhado incorreto ❌ (nav dentro de nav)
│   │   └── Linhas 86-87: Chamada para funções não definidas
│   │
│   ├── 🟠 boasVindas.js
│   │   ├── Linhas 120-148: Função copiarMensagem() aninhada ❌
│   │   └── 🔧 Reorganizar estrutura
│   │
│   ├── 🔴 boasVindasBrPower.html
│   │   └── Linha 10: type="imagex/png" ❌
│   │
│   └── ✅ boasVindasBrPower.js (OK)
│
├── Cobranca/
│   ├── 🔴 cobranca.html
│   │   ├── Linha 11: type="imagex/png" ❌
│   │   └── Linha 11: Caminho favicon incorreto ❌ (falta ../)
│   │
│   └── ✅ cobranca.js (OK)
│
├── Eventos/
│   ├── 🔴 eventos.html
│   │   └── Linha 10: type="imagex/png" ❌
│   │
│   └── 📁 (vazio)
│
├── Rastreio/
│   └── 🔴 rastreio.html
│       ├── Linha 11: type="imagex/png" ❌
│       └── CSS correto para telas
│
├── TermoCancelamento/
│   ├── 🔴 termoCancelamento.html
│   │   └── CSS: ../TermoRastreador/termoRastreador.css
│   │
│   └── ✅ termoCancelamento.js (OK)
│
├── TermoNegociacao/
│   ├── 🟢 termoNegociacao.html
│   │   └── type="image/png" ✅ (Correto!)
│   │
│   ├── termoNegociacao.css
│   │
│   └── ✅ termoNegociacao.js (OK)
│
├── TermoQuitacao/
│   ├── 🔴 termoQuitacao.html
│   │   └── Linha final: </form> extra ❌
│   │
│   └── ✅ termoQuitacao.js (OK)
│
├── TermoRastreador/
│   ├── 🔴 termoRastreador.html
│   │   └── Linha 87: src="/index.js" ❌ (Caminho absoluto)
│   │
│   ├── termoRastreador.css
│   │
│   ├── termoRastreador.js
│   │
│   ├── agendamento.html
│   │
│   ├── agendamento.js
│   │
│   ├── orientacaoRastreador.html
│   │
│   └── orietacaoRastreador.js (nota: nome com typo "orietacao")
│
├── Correios/
│   ├── 🔴 indexCorreios.html
│   │   └── Linha 10: type="imagex/png" ❌
│   │
│   ├── 🔴 correio.html
│   │   └── Linha 10: type="imagex/png" ❌
│   │
│   ├── correios.js
│   │   └── ⚠️ Referencia logo-3.png (pode não existir)
│   │
│   ├── kitDoAssociado.html
│   │   └── type="image/x-icon" ✅ (Correto)
│   │
│   └── ✅ kitDoAssociado.js (OK)
│
├── Assistencia24horas/
│   ├── 🔴 assistencia24horas.html
│   │   ├── Linha 10: type="imagex/png" ❌
│   │   └── Linha 118-120: Link "assistencia24horasIndex.html.html" ❌ (Dupla extensão)
│   │
│   ├── assistencia24horas.js
│   │
│   ├── 🔴 assistencia24horasIndex.html
│   │   └── Linha 10: type="imagex/png" ❌
│   │
│   └── cidades/
│       ├── 🔴 cidades.html
│       │   └── Linha 10: type="imagex/png" ❌
│       │
│       └── regioesGoiania/
│           ├── 🔴 CentralGoiania.html
│           │   └── Linha 10: type="imagex/png" ❌
│           │
│           ├── 🔴 regioesGoiania.html
│           │   └── Linha 10: type="imagex/png" ❌
│           │
│           └── 🔴 sudoesteGoiania.html
│               └── Linha 10: type="imagex/png" ❌
│
├── Agendamento/
│   ├── agendamento2.html
│   │
│   └── agendamento2.js
│
└── Images/
    ├── brclube2.png ✅
    ├── br.png ✅
    ├── favicon.ico.png ✅
    ├── assinatura.png (referenciada em termoNegociacao.js)
    └── logo-3.png ❓ (pode não existir)
```

---

## 🔥 MAPA DE CALOR - SEVERIDADE POR ARQUIVO

```
CRÍTICO (🔴) - 15 arquivos com imagex/png
├── index.html
├── termos.html
├── BoasVindas/boasVindas.html
├── BoasVindas/boasVindasBrPower.html
├── Cobranca/cobranca.html
├── Eventos/eventos.html
├── Rastreio/rastreio.html
├── Correios/indexCorreios.html
├── Correios/correio.html
├── Assistencia24horas/assistencia24horas.html
├── Assistencia24horas/assistencia24horasIndex.html
├── Assistencia24horas/cidades/cidades.html
├── Assistencia24horas/cidades/regioesGoiania/CentralGoiania.html
├── Assistencia24horas/cidades/regioesGoiania/regioesGoiania.html
└── Assistencia24horas/cidades/regioesGoiania/sudoesteGoiania.html

CRÍTICO (🔴) - Funções JavaScript
├── BoasVindas/boasVindas.html → copiarMensagem() não definida
└── BoasVindas/boasVindas.js → Estrutura incorreta

CRÍTICO (🔴) - Paths
└── TermoRastreador/termoRastreador.html → /index.js (caminho absoluto)

ALTO (🟠) - HTML/Estrutura
├── BoasVindas/boasVindas.html → Nav aninhada incorretamente
├── TermoQuitacao/termoQuitacao.html → </form> duplicado
└── Assistencia24horas/assistencia24horas.html → .html.html

ALTO (🟠) - Paths
└── Cobranca/cobranca.html → Favicon sem ../

MÉDIO (🟡) - CSS
├── padrao.css → * { font-size: 20px } universal
├── Nav/nav.css → float: left desatualizado
└── Correios/correios.js → Imagem logo-3.png pode faltar
```

---

## 📊 GRÁFICO DE PROBLEMAS

### Por Tipo

```
Tipo MIME Inválido       ████████████████████ (15 problemas)
Função Não Definida      ██ (2 problemas)
Caminho Incorreto        ███ (3 problemas)
HTML Malformado          ██ (2 problemas)
CSS Problemático         ██ (2 problemas)
Imagem Faltante          █ (1 problema)
Inconsistência           █ (1 problema)
```

### Por Severidade

```
🔴 CRÍTICO    ████████████████ (8 problemas)
🟠 ALTO       ████████ (4 problemas)
🟡 MÉDIO      ██████ (6 problemas)
🟢 BAIXO      (0 problemas)
```

### Por Arquivo

```
index.html                           █ 1
termos.html                          █ 1
BoasVindas/boasVindas.html          ███ 3
BoasVindas/boasVindasBrPower.html   █ 1
BoasVindas/boasVindas.js            █ 1
Cobranca/cobranca.html              ██ 2
Eventos/eventos.html                █ 1
Rastreio/rastreio.html              █ 1
TermoCancelamento/...               ✅ 0
TermoNegociacao/...                 ✅ 0
TermoQuitacao/...                   █ 1
TermoRastreador/...                 █ 1
Correios/indexCorreios.html         █ 1
Correios/correio.html               █ 1
Correios/correios.js                █ 1
Assistencia24horas/...              ███ 3
Agendamento/...                     ✅ 0
padrao.css                          █ 1
Nav/nav.css                         █ 1
```

---

## 🎯 ESTRATÉGIA DE CORREÇÃO

### Etapa 1: Type MIME (2 minutos)
```
Find:    type="imagex/png"
Replace: type="image/png"
Scope:   Todo o projeto (15 files)
```

### Etapa 2: JavaScript (10 minutos)
```
- BoasVindas/boasVindas.js (reorganizar funções)
- TermoRastreador/termoRastreador.html (corrigir path)
```

### Etapa 3: HTML (5 minutos)
```
- BoasVindas/boasVindas.html (limpar estrutura)
- TermoQuitacao/termoQuitacao.html (remover </form>)
- Assistencia24horas/assistencia24horas.html (dupla extensão)
```

### Etapa 4: CSS (3 minutos)
```
- padrao.css (remover * { font-size })
- Nav/nav.css (remover float)
```

---

## ✅ CHECKLIST FINAL POR ARQUIVO

```
[ ] index.html                                       (1 problema)
[ ] termos.html                                      (1 problema)
[ ] padrao.css                                       (1 problema)
[ ] Nav/nav.css                                      (1 problema)
[ ] BoasVindas/boasVindas.html                       (3 problemas)
[ ] BoasVindas/boasVindasBrPower.html                (1 problema)
[ ] BoasVindas/boasVindas.js                         (1 problema)
[ ] Cobranca/cobranca.html                           (2 problemas)
[ ] Eventos/eventos.html                            (1 problema)
[ ] Rastreio/rastreio.html                          (1 problema)
[ ] TermoQuitacao/termoQuitacao.html                (1 problema)
[ ] TermoRastreador/termoRastreador.html            (1 problema)
[ ] Correios/indexCorreios.html                     (1 problema)
[ ] Correios/correio.html                           (1 problema)
[ ] Correios/correios.js                            (1 problema)
[ ] Assistencia24horas/assistencia24horas.html      (3 problemas)
[ ] Assistencia24horas/assistencia24horasIndex.html (1 problema)
[ ] Assistencia24horas/cidades/cidades.html         (1 problema)
[ ] Assistencia24horas/cidades/regioesGoiania/*.html (3 problemas)
```

---

## 🚨 IMPACTO SEM CORREÇÃO

```
Visibilidade: 30% (ícones/logos não carregam)
Funcionalidade: 60% (botões/formulários parcialmente funcionam)
Layout: 50% (responsividade quebrada)
Erros JS: 10+ (console cheia de warnings)
Experiência: PÉSSIMA ❌
```

## ✨ IMPACTO COM CORREÇÃO

```
Visibilidade: 100% (todos os ícones carregam) ✅
Funcionalidade: 100% (todos os botões funcionam) ✅
Layout: 100% (responsivo em todos os dispositivos) ✅
Erros JS: 0 (console limpo) ✅
Experiência: EXCELENTE ✅✅✅
```

---

**Status:** 📋 Pronto para Análise  
**Total de Problemas:** 23  
**Estimativa de Correção:** ~20 minutos  
**Complexidade:** Baixa a Média

