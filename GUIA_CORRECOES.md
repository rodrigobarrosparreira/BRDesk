# GUIA DE CORREÇÕES - BR CLUBE FRONTEND

## Como Usar Este Guia

Este documento contém **instruções passo a passo** para corrigir todos os 23 problemas identificados no frontend do BR CLUBE.

---

## CORREÇÃO 1: Type MIME Inválido (15 arquivos)

**Problema:** `type="imagex/png"` deve ser `type="image/png"`

### Arquivos a Corrigir:

```
1. index.html (linha 10)
2. termos.html (linha 11)
3. BoasVindas/boasVindas.html (linha 10)
4. BoasVindas/boasVindasBrPower.html (linha 10)
5. Cobranca/cobranca.html (linha 11)
6. Eventos/eventos.html (linha 10)
7. Rastreio/rastreio.html (linha 11)
8. Correios/indexCorreios.html (linha 10)
9. Correios/correio.html (linha 10)
10. Assistencia24horas/assistencia24horas.html (linha 10)
11. Assistencia24horas/assistencia24horasIndex.html (linha 10)
12. Assistencia24horas/cidades/cidades.html (linha 10)
13. Assistencia24horas/cidades/regioesGoiania/CentralGoiania.html (linha 10)
14. Assistencia24horas/cidades/regioesGoiania/regioesGoiania.html (linha 10)
15. Assistencia24horas/cidades/regioesGoiania/sudoesteGoiania.html (linha 10)
```

### Substituição Global:

**Buscar:** `type="imagex/png"`  
**Substituir por:** `type="image/png"`

### Em VS Code:
1. Pressione `Ctrl+H` (Find and Replace)
2. Campo "Find": `type="imagex/png"`
3. Campo "Replace": `type="image/png"`
4. Clique em "Replace All"

---

## CORREÇÃO 2: Reorganizar Funções JavaScript em boasVindas.js

**Arquivo:** `BoasVindas/boasVindas.js`

**Problema:** A função `copiarMensagem()` está aninhada dentro de `limparFormulario()`, tornando-a inacessível globalmente.

### Solução:

O arquivo deve ter esta estrutura:

```javascript
function enviarFormulario() {
  // ... código existente ...
}

function limparFormulario() {
  // Campos de texto
  ['nome','placa','boleto','telefone','endereco','cep','email'].forEach(id => {
    const el = document.getElementById(id);
    if (el) el.value = '';
  });

  // Select forma de pagamento
  const forma = document.getElementById('formaPagamento');
  if (forma) forma.value = '';

  // Radios de gênero
  const marcado = document.querySelector('input[name="genero"]:checked');
  if (marcado) marcado.checked = false;

  // Mensagem exibida
  const out = document.getElementById('texto');
  if (out) out.innerHTML = '';

  console.log("Formulário limpo!");
}

function copiarMensagem() {
  const out = document.getElementById('texto');
  if (!out || !out.innerText.trim()) {
    alert('Gere a mensagem antes de copiar.');
    return;
  }
  const textoPlano = out.innerText.replace(/\n{3,}/g, '\n\n').trim();
  navigator.clipboard.writeText(textoPlano)
    .then(() => alert('Mensagem copiada!'))
    .catch(() => alert('Não foi possível copiar automaticamente. Selecione e copie manualmente.'));
}
```

---

## CORREÇÃO 3: Caminho Incorreto de Script em termoRastreador.html

**Arquivo:** `TermoRastreador/termoRastreador.html`

**Problema:** `<script src="/index.js"></script>` começa com `/` (caminho absoluto)

### Substituição:

**Buscar:** 
```html
    <script src="/index.js"></script>
```

**Substituir por:**
```html
    <script src="../index.js"></script>
```

---

## CORREÇÃO 4: Remover Form Duplicado em termoQuitacao.html

**Arquivo:** `TermoQuitacao/termoQuitacao.html`

**Problema:** Há um `</form>` extra no final do arquivo (última linha antes do `</html>`)

### Código Atual (ERRADO):
```html
    <script src="termoQuitacao.js"></script>
    <script src="../index.js"></script>
    </form>  <!-- ❌ REMOVER ESTA LINHA -->

</body>

</html>
```

### Código Correto:
```html
    <script src="termoQuitacao.js"></script>
    <script src="../index.js"></script>

</body>

</html>
```

---

## CORREÇÃO 5: Estrutura HTML Incorreta em boasVindas.html

**Arquivo:** `BoasVindas/boasVindas.html`

**Problema:** Tag `<nav>` contém `<header>` e outra `<nav>` aninhada. Estrutura DOM inválida.

### Código Atual (ERRADO):
```html
    <nav>
        <!-- Adicione a imagem da logo -->
        <header class="site-header">
  <div class="brand">
    <img src="../Images/brclube2.png" alt="BR Clube" class="logo" />
  </div>
      <nav class="mainnav">
        <ul>
           <li><a target="_blank" href="../index.html">Menu</a></li>
           <li><a target="_blank" href="https://portal.sivisweb.com.br/loja/012/dashboard">Portal</a></li>
           <li><a target="_blank" href="https://mail.google.com">Workspace</a></li>
           <li><a target="_blank" href="https://painel.multi360.com.br">Multi360</a></li>
           <li><a target="_blank" href="https://sivisweb.com.br/login.php?ex=1&emp=013">SIVIS Br Clube</a></li>
           <li><a target="_blank" href="https://sivisweb.com.br/login.php?ex=1&emp=013">SIVIS Left</a></li>
        </ul>
  </nav>
</header>
        
        <h1>MENSAGEM DE BOAS-VINDAS</h1>
    </header>
```

### Código Correto:
```html
    <nav>
        <!-- Adicione a imagem da logo -->
        <img src="../Images/brclube2.png" alt="BR Clube" class="logo" />

        <ul>
           <li><a href="../index.html">Menu</a></li>
           <li><a target="_blank" href="https://portal.sivisweb.com.br/loja/012/dashboard">Portal</a></li>
           <li><a target="_blank" href="https://mail.google.com">Workspace</a></li>
           <li><a target="_blank" href="https://painel.multi360.com.br">Multi360</a></li>
           <li><a target="_blank" href="https://sivisweb.com.br/login.php?ex=1&emp=013">SIVIS Br Clube</a></li>
           <li><a target="_blank" href="https://sivisweb.com.br/login.php?ex=1&emp=013">SIVIS Left</a></li>
        </ul>
    </nav>

    <h1>MENSAGEM DE BOAS-VINDAS</h1>
```

---

## CORREÇÃO 6: Link com Dupla Extensão .html.html

**Arquivo:** `Assistencia24horas/assistencia24horas.html`

**Problema:** Link aponta para `assistencia24horasIndex.html.html` (extensão duplicada)

### Código Atual (ERRADO):
```html
                <a href="../Assistencia24horas/assistencia24horasIndex.html.html">
                    <h3>LOCALIZAR PRESTADORES</h3>
                </a>
```

### Código Correto:
```html
                <a href="../Assistencia24horas/assistencia24horasIndex.html">
                    <h3>LOCALIZAR PRESTADORES</h3>
                </a>
```

---

## CORREÇÃO 7: Caminho Incorreto de Favicon em cobranca.html

**Arquivo:** `Cobranca/cobranca.html`

**Problema:** Favicon está em `Cobranca/` mas deveria referenciar `../Images/`

### Código Atual (ERRADO):
```html
<link rel="shortcut icon" type="imagex/png" href="Images/favicon.ico.png">
```

### Código Correto:
```html
<link rel="shortcut icon" type="image/png" href="../Images/favicon.ico.png">
```

---

## CORREÇÃO 8: Remover Regra CSS Universal

**Arquivo:** `padrao.css`

**Problema:** `* { font-size: 20px; }` sobrescreve TODOS os tamanhos de fonte

### Código Atual (ERRADO):
```css
* {
    font-size: 20px;
}

header {
    background-color: #000056;
    text-align: center;
}
```

### Código Correto:
```css
header {
    background-color: #000056;
    text-align: center;
}
```

**Remover as linhas 1-2 completamente.**

---

## CORREÇÃO 9: Remover Float em nav.css

**Arquivo:** `Nav/nav.css`

**Problema:** `float: left` é técnica desatualizada e conflita com flexbox

### Código Atual (ERRADO):
```css
li {
    float: left;
}

li a {
    display: block;
    color: rgb(255, 255, 255);
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-weight: bold;
    font-size: 25px;
}
```

### Código Correto:
```css
li {
    /* Remover float - deixar flexbox fazer o trabalho */
}

li a {
    display: block;
    color: rgb(255, 255, 255);
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-weight: bold;
    font-size: 25px;
}
```

---

## CORREÇÃO 10: Verificar Imagens em correios.js

**Arquivo:** `Correios/correios.js`

**Problema:** Referencia `../Images/logo-3.png` que pode não existir

### Verificar:
1. Abra a pasta `Images/`
2. Procure por arquivo `logo-3.png`
3. Se não existir, substitua por `brclube2.png` que é usada em outras páginas

### Código Atual:
```javascript
informacoes += `<img src="../Images/logo-3.png" alt="Logo Destinatário" style="width: 80px; height: auto;"><br>`;
```

### Código Alternativo (se logo-3.png não existir):
```javascript
informacoes += `<img src="../Images/brclube2.png" alt="Logo Destinatário" style="width: 80px; height: auto;"><br>`;
```

---

## ORDEM DE EXECUÇÃO RECOMENDADA

### Fase 1 - CRÍTICO (15 minutos)
1. ✅ Correção 1: Type MIME (Buscar e Substituir Global)
2. ✅ Correção 2: boasVindas.js
3. ✅ Correção 3: termoRastreador.html

### Fase 2 - ALTO (20 minutos)
4. ✅ Correção 4: termoQuitacao.html
5. ✅ Correção 5: boasVindas.html
6. ✅ Correção 6: assistencia24horas.html

### Fase 3 - MÉDIO (15 minutos)
7. ✅ Correção 7: cobranca.html
8. ✅ Correção 8: padrao.css
9. ✅ Correção 9: nav.css
10. ✅ Correção 10: correios.js

---

## TESTES APÓS AS CORREÇÕES

1. **Abrir cada página** e verificar no console (F12) se há erros
2. **Testar formulários** - clicar em botões para garantir que funcionam
3. **Testar responsividade** - redimensionar navegador para testar em dispositivos pequenos
4. **Testar links** - clicar em links de navegação para garantir que funcionam
5. **Validar HTML** - usar [validator.w3.org](https://validator.w3.org/)

---

## CHECKLIST FINAL

- [ ] Todos os `type="imagex/png"` foram corrigidos para `type="image/png"`
- [ ] Funções em `boasVindas.js` foram reorganizadas
- [ ] Script path em `termoRastreador.html` foi corrigido
- [ ] Form duplicado foi removido de `termoQuitacao.html`
- [ ] Estrutura HTML de `boasVindas.html` foi corrigida
- [ ] Link `.html.html` foi corrigido em `assistencia24horas.html`
- [ ] CSS universal foi removido de `padrao.css`
- [ ] Float foi removido de `nav.css`
- [ ] Imagens foram verificadas em `correios.js`
- [ ] Todos os testes passaram ✅

---

## SUPORTE

Em caso de dúvidas:
1. Consulte o RELATÓRIO_PROBLEMAS_FRONTEND.md para mais detalhes
2. Verifique o console do navegador (F12) para mensagens de erro
3. Valide o HTML em validator.w3.org

**Fim do Guia de Correções**
