<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yung Redação - Preview</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f0f2f5;
            margin: 0;
        }

        .container {
            text-align: center;
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            width: 80%;
            max-width: 600px;
        }

        /* Simulador do Editor da Plataforma */
        .ql-editor {
            border: 2px dashed #ccc;
            padding: 20px;
            min-height: 150px;
            margin-top: 20px;
            border-radius: 8px;
            outline: none;
            background: #fafafa;
        }

        .ql-editor:focus {
            border-color: #ff416c;
            background: #fff;
        }

        h1 { color: #333; }
        p { color: #666; }
    </style>
</head>
<body>

    <div class="container">
        <h1>Yung Redação</h1>
        <p>Este é um simulador. O botão de injeção aparecerá fixo no rodapé.</p>
        
        <div class="ql-editor" contenteditable="true" placeholder="O texto aparecerá aqui..."></div>
    </div>

    <script>
        // O código que você enviou adaptado para rodar no carregamento da página
        (function(){
            var b = document.createElement('div');
            b.id = 'btn-inj';
            b.innerHTML = 'INJETAR CONTEÚDO';

            /* Estilo Visual Profissional */
            var style = 'position:fixed; bottom:30px; left:50%; transform:translateX(-50%); z-index:999999; ' +
                        'background: linear-gradient(135deg, #ff4b2b, #ff416c); color:white; ' +
                        'padding: 14px 40px; font-weight: 800; border-radius: 50px; ' +
                        'box-shadow: 0 10px 20px rgba(255, 75, 43, 0.3); font-family: "Segoe UI", Tahoma, sans-serif; ' +
                        'cursor:pointer; border: 2px solid rgba(255,255,255,0.2); transition: all 0.3s ease; ' +
                        'text-transform: uppercase; letter-spacing: 1px; user-select: none;';
            b.style = style;

            /* Efeitos de Hover */
            b.onmouseover = function() { 
                this.style.transform = 'translateX(-50%) scale(1.05)'; 
                this.style.boxShadow = '0 15px 25px rgba(255, 75, 43, 0.4)'; 
            };
            b.onmouseout = function() { 
                this.style.transform = 'translateX(-50%) scale(1)'; 
                this.style.boxShadow = '0 10px 20px rgba(255, 75, 43, 0.3)'; 
            };

            document.body.appendChild(b);

            b.onclick = function(){
                var t = prompt('yung redação');
                if(!t) return;

                // Tenta focar no editor simulado
                var e = document.querySelector('.ql-editor');
                
                if(e){
                    e.focus();
                    document.execCommand('insertText', false, t);
                    // Dispara o evento de input para o sistema entender que houve mudança
                    e.dispatchEvent(new Event('input', { bubbles: true }));
                    alert('Injetado com sucesso!');
                } else {
                    alert('Erro: Editor não encontrado.');
                }
            };
        })();
    </script>
</body>
</html>

