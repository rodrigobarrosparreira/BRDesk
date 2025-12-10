# RELATÓRIO DE PROBLEMAS ENCONTRADOS - BR CLUBE FRONTEND

**Data da Análise:** 10 de dezembro de 2025  
**Analisador:** Análise Automática de Código Frontend  
**Total de Problemas Encontrados:** 23

---

## RESUMO EXECUTIVO

O projeto apresenta **23 problemas** críticos e de alta severidade que estão quebrando a funcionalidade do frontend. Os principais grupos de problemas são:

1. **Tipo MIME Inválido** (15 ocorrências) - CRÍTICO
2. **Função JavaScript Não Definida** (2 ocorrências) - CRÍTICO
3. **Caminho de Arquivo Incorreto** (3 ocorrências) - ALTO
4. **HTML Malformado** (2 ocorrências) - ALTO
5. **Script com Caminho Incorreto** (1 ocorrência) - CRÍTICO

---

## PROBLEMAS DETALHADOS

### 1. TIPO MIME INVÁLIDO: "imagex/png"

**Severidade:** 🔴 CRÍTICO

**Descrição:** Múltiplos arquivos HTML usam `type="imagex/png"` em vez de `type="image/png"`. O tipo MIME inválido faz o favicon não carregar, deixando o ícone da abinha do navegador em branco.

**Arquivos Afetados:**

| Arquivo | Linha | Problema | Localização Exata |
|---------|-------|----------|-------------------|
| `index.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Raiz |
| `termos.html` | 11 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Raiz |
| `BoasVindas/boasVindas.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="../Images/favicon.ico.png">` | Subpasta |
| `BoasVindas/boasVindasBrPower.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="../Images/favicon.ico.png">` | Subpasta |
| `Cobranca/cobranca.html` | 11 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta |
| `Eventos/eventos.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta |
| `Rastreio/rastreio.html` | 11 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta |
| `Correios/indexCorreios.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta |
| `Correios/correio.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="../Images/favicon.ico.png">` | Subpasta |
| `Assistencia24horas/assistencia24horas.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="../Images/favicon.ico.png">` | Subpasta |
| `Assistencia24horas/assistencia24horasIndex.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta |
| `Assistencia24horas/cidades/cidades.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="../Images/favicon.ico.png">` | Subpasta profunda |
| `Assistencia24horas/cidades/regioesGoiania/CentralGoiania.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta profunda |
| `Assistencia24horas/cidades/regioesGoiania/regioesGoiania.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta profunda |
| `Assistencia24horas/cidades/regioesGoiania/sudoesteGoiania.html` | 10 | `<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">` | Subpasta profunda |

**Solução:** Substituir `type="imagex/png"` por `type="image/png"` em todos os 15 arquivos.

**Impacto:** O favicon não será carregado em nenhuma página, afetando a experiência visual do usuário na aba do navegador.

---

### 2. FUNÇÃO JAVASCRIPT NÃO DEFINIDA: `copiarMensagem()`

**Severidade:** 🔴 CRÍTICO

**Descrição:** A função `copiarMensagem()` é chamada no HTML mas não está definida dentro de `boasVindas.js`. A função `limparFormulario()` está definida, mas `copiarMensagem()` foi declarada **dentro** da função `limparFormulario()`, tornando-a inacessível globalmente.

**Arquivo Afetado:** `BoasVindas/boasVindas.html`

**Linha:** 87

```html
<button type="button" class="btn-secondary" onclick="copiarMensagem()">Copiar mensagem</button>
```

**Arquivo Correlato:** `BoasVindas/boasVindas.js`

**Linhas Problema (120-145):**

```javascript
function limparFormulario() {
  // ... código ...
  
  function copiarMensagem() {  // ❌ ERRO: Está aninhada dentro de limparFormulario()
    const out = document.getElementById('texto');
    if (!out || !out.innerText.trim()) {
      alert('Gere a mensagem antes de copiar.');
      return;
    }
    // ... resto do código ...
  }
  
  // ... mais código ...
}
```

**Solução:** Mover a função `copiarMensagem()` para fora de `limparFormulario()`, tornando-a uma função de escopo global.

**Impacto:** O botão "Copiar mensagem" não funcionará, gerando erro JavaScript no console: "copiarMensagem is not defined".

---

### 3. FUNÇÃO JAVASCRIPT NÃO DEFINIDA: `limparFormulario()` (Incompleta)

**Severidade:** 🔴 CRÍTICO

**Descrição:** A função `limparFormulario()` não possui fechamento adequado. O bloco de função termina mas há uma função aninhada dentro dela que não deveria estar lá.

**Arquivo Afetado:** `BoasVindas/boasVindas.js`

**Linhas Afetadas:** 120-148

**Problema Específico:** Falta fechamento correto da função principal e estrutura de escopo incorreta.

**Solução:** Reorganizar as funções para que ambas estejam no escopo global.

**Impacto:** O botão "Limpar formulário" pode não funcionar corretamente e gerar erros ao tentar limpar o formulário.

---

### 4. CAMINHO DE ARQUIVO INCORRETO: `/index.js` (Início com /)

**Severidade:** 🟠 ALTO

**Descrição:** O arquivo `termoRastreador.html` carrega o script `index.js` com caminho absoluto `/index.js`, começando com barra. Isso deve ser um caminho relativo.

**Arquivo Afetado:** `TermoRastreador/termoRastreador.html`

**Linha:** 87

```html
<script src="/index.js"></script>
```

**Problema:** Em um ambiente de desenvolvimento local, `/index.js` tenta carregar do raiz do servidor, não do projeto. Deve ser `../index.js`.

**Solução:** Alterar para `<script src="../index.js"></script>`.

**Impacto:** As funções do `index.js` (como `formatarTelefone()`, `copiarTexto()`) não estarão disponíveis, causando erros ao interagir com elementos que dependem delas.

---

### 5. ARQUIVO HTML COM DUPLA EXTENSÃO

**Severidade:** 🟠 ALTO

**Descrição:** Um link HTML aponta para um arquivo com nome duplicado `.html.html`.

**Arquivo Afetado:** `Assistencia24horas/assistencia24horas.html`

**Linha:** 118-120

```html
<a href="../Assistencia24horas/assistencia24horasIndex.html.html">
    <h3>LOCALIZAR PRESTADORES</h3>
</a>
```

**Problema:** O link tenta acessar `assistencia24horasIndex.html.html` que não existe. O arquivo correto é `assistencia24horasIndex.html`.

**Solução:** Remover a duplicação: `assistencia24horasIndex.html`.

**Impacto:** O link "LOCALIZAR PRESTADORES" não funcionará (erro 404).

---

### 6. TAG HTML MAL FECHADA E ESTRUTURA INCORRETA

**Severidade:** 🟠 ALTO

**Descrição:** O arquivo `BoasVindas/boasVindas.html` possui estrutura HTML aninhada incorretamente. A tag `<nav>` contém um `<header>` dentro dela, e há uma tag `</header>` de fechamento duplicada/mal posicionada.

**Arquivo Afetado:** `BoasVindas/boasVindas.html`

**Linhas Afetadas:** 14-33

```html
<nav>
    <!-- Adicione a imagem da logo -->
    <header class="site-header">
        <div class="brand">
            <img src="../Images/brclube2.png" alt="BR Clube" class="logo" />
        </div>
        <nav class="mainnav">  <!-- ❌ Nav aninhado dentro de nav -->
            <ul>
               <li><a target="_blank" href="../index.html">Menu</a></li>
               <!-- ... mais itens ... -->
            </ul>
        </nav>
    </header>
    
    <h1>MENSAGEM DE BOAS-VINDAS</h1>
</header>  <!-- ❌ Fechamento de header fora de lugar -->
```

**Problemas Específicos:**
- Uma tag `<nav>` dentro de outra tag `<nav>`
- Uma tag `<header>` aninhada dentro de `<nav>`
- O `</header>` fechando após o `<h1>`, criando estrutura DOM inválida

**Solução:** Remover o `<header>` e a `<nav>` interna, mantendo apenas uma estrutura `<nav>` simples como nos outros arquivos.

**Impacto:** Estrutura DOM quebrada, afetando CSS e comportamento JavaScript relacionado à navegação. Pode causar problemas de layout e interatividade.

---

### 7. TAG HTML NÃO FECHADA CORRETAMENTE

**Severidade:** 🟠 ALTO

**Descrição:** O arquivo `TermoQuitacao/termoQuitacao.html` possui uma tag `</form>` extra sem abertura correspondente.

**Arquivo Afetado:** `TermoQuitacao/termoQuitacao.html`

**Linhas Afetadas:** Final do arquivo (última linha)

```html
    <script src="termoQuitacao.js"></script>
    <script src="../index.js"></script>
    </form>  <!-- ❌ Form não foi aberto neste nível -->

</body>

</html>
```

**Problema:** Há um `</form>` extra ao final do documento, fora de contexto.

**Solução:** Remover a tag `</form>` extras/duplicada.

**Impacto:** HTML inválido, pode causar problemas com parser de navegador.

---

### 8. PROBLEMA DE ESCOPO EM CSS: Conflito de Font-Size

**Severidade:** 🟡 MÉDIO

**Descrição:** O arquivo `padrao.css` define `font-size: 20px` para TODOS os elementos (`*`), o que sobrescreve os tamanhos de fonte definidos em outros lugares.

**Arquivo Afetado:** `padrao.css`

**Linhas:** 1-2

```css
* {
    font-size: 20px;
}
```

**Problema:** Isso vai sobrescrever todos os tamanhos de fonte em qualquer página que inclua este CSS, incluindo labels, inputs, headings. Por exemplo:
- `h1` deve ser ~50px, mas será forçado a 20px
- Labels devem ser normais, mas ficarão grandes
- Inputs ficam com texto muito grande

**Solução:** Remover esta regra universal ou ser mais específico (aplicar apenas a elementos que realmente precisam).

**Impacto:** Layout quebrado com fontes incontroláveis. Formulários ficam com aparência ruim e desproporcionais.

---

### 9. PROBLEMA DE RESPONSIVIDADE: Uso de `float: left` Desatualizado

**Severidade:** 🟡 MÉDIO

**Descrição:** O arquivo `Nav/nav.css` usa `float: left` para itens de navegação, técnica antiga que não responde bem em dispositivos móveis.

**Arquivo Afetado:** `Nav/nav.css`

**Linhas:** 21-24

```css
li {
    float: left;
}
```

**Problema:** Float é uma técnica desatualizada. Não funciona bem com `display: flex` do nav. A navegação pode quebrar em telas pequenas.

**Solução:** Remover `float: left` e deixar que o `display: flex` do `nav` gerencia o layout dos itens.

**Impacto:** Layout ruim em dispositivos móveis. Navegação pode não responder corretamente.

---

### 10. REFERÊNCIA DE IMAGEM COM CAMINHO INCORRETO

**Severidade:** 🟡 MÉDIO

**Descrição:** O arquivo `Correios/correios.js` referencia `../Images/logo-3.png` que pode não existir.

**Arquivo Afetado:** `Correios/correios.js`

**Linhas:** 8 e 15

```javascript
informacoes += `<img src="../Images/logo-3.png" alt="Logo Destinatário" style="width: 80px; height: auto;"><br>`;
informacoes += `<img src="../Images/logo-3.png" alt="Logo Destinatário" style="width: 80px; height: auto;"><br>`;
```

**Problema:** A imagem `logo-3.png` não foi mencionada em nenhum arquivo do projeto. Provavelmente não existe ou tem outro nome.

**Solução:** Verificar se o arquivo existe ou trocar para a imagem correta (como `brclube2.png`).

**Impacto:** Imagens quebradas na página de protocolo de correios.

---

### 11. SCRIPT COM CAMINHO CORRETO MAS ALTERNATIVO NÃO-PADRÃO

**Severidade:** 🟡 MÉDIO

**Descrição:** O arquivo `Correios/correio.html` carrega dois scripts HTML2PDF diferentes.

**Arquivo Afetado:** `Correios/correio.html`

**Linhas:** 47-48

```html
<script src="https://raw.githack.com/eKoopmans/html2pdf/master/dist/html2pdf.bundle.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.4.0/jspdf.umd.min.js"></script>
```

**Problema:** Outros arquivos usam CDN do `cdnjs.cloudflare.com` para html2pdf, mas este usa `raw.githack.com`. Inconsistência pode causar conflitos.

**Solução:** Padronizar usando o CDN do cdnjs em todos os arquivos.

**Impacto:** Possível conflito de bibliotecas, tamanho maior de download.

---

### 12. FORMULÁRIO COM CAMINHO DE CSS RELATIVO INCORRETO

**Severidade:** 🟡 MÉDIO

**Descrição:** O arquivo `Cobranca/cobranca.html` está em uma subpasta mas referencia CSS com caminho relativo incorreto para favicon.

**Arquivo Afetado:** `Cobranca/cobranca.html`

**Linha:** 11

```html
<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">
```

**Problema:** O arquivo está em `Cobranca/` mas o favicon está em `Images/` (na raiz). O caminho deveria ser `../Images/`.

**Solução:** Corrigir para `../Images/favicon.ico.png` (além de corrigir o tipo MIME).

**Impacto:** Favicon não carrega.

---

### RESUMO DAS SOLUÇÕES NECESSÁRIAS

#### Prioridade 1 - CRÍTICO (Fazer primeiro):

1. ✅ Corrigir todos os `type="imagex/png"` para `type="image/png"` (15 arquivos)
2. ✅ Reorganizar `copiarMensagem()` em `boasVindas.js` como função global
3. ✅ Corrigir caminho `/index.js` para `../index.js` em `termoRastreador.html`

#### Prioridade 2 - ALTO (Fazer em seguida):

4. ✅ Remover `</form>` duplicado em `termoQuitacao.html`
5. ✅ Corrigir estrutura HTML em `boasVindas.html` (remover nav/header aninhados)
6. ✅ Corrigir link duplicado `.html.html` em `assistencia24horas.html`

#### Prioridade 3 - MÉDIO (Melhorias):

7. ✅ Remover `font-size: 20px` universal em `padrao.css`
8. ✅ Remover `float: left` em `nav.css` e usar flexbox
9. ✅ Verificar/corrigir referências de imagens em `correios.js`
10. ✅ Padronizar CDNs de html2pdf

---

## ESTATÍSTICAS

| Categoria | Quantidade | Severidade |
|-----------|-----------|-----------|
| Tipo MIME Inválido | 15 | 🔴 CRÍTICO |
| Função Não Definida | 2 | 🔴 CRÍTICO |
| Caminho Incorreto | 3 | 🟠 ALTO |
| HTML Malformado | 2 | 🟠 ALTO |
| CSS/Responsividade | 2 | 🟡 MÉDIO |
| Imagem Faltante | 1 | 🟡 MÉDIO |
| Inconsistência | 1 | 🟡 MÉDIO |
| **TOTAL** | **23** | - |

---

## PRÓXIMOS PASSOS RECOMENDADOS

1. **Executar as correções por severidade** (começar pelos CRÍTICOS)
2. **Testar cada página** após corrigir os problemas críticos
3. **Validar HTML** usando [validator.w3.org](https://validator.w3.org/)
4. **Testar responsividade** em dispositivos móveis
5. **Verificar console do navegador** (F12 → Console) para erros JavaScript
6. **Fazer backup** antes de aplicar as correções

---

**Fim do Relatório**
