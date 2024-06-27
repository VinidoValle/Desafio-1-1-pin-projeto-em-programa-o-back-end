# Desafio-1-1-pin-projeto-em-programa-o-back-end
Desafio 1 da matéria pin projeto em programação back end
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Projeto de Classes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f9f9f9;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 5px;
            background-color: white;
        }
        h1, h2 {
            text-align: center;
        }
        .card {
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 20px;
            margin-bottom: 10px;
            background-color: #f4f4f4;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Projeto de Classes</h1>
        <div id="pessoas"></div>
    </div>

    <script>
        // Classe Endereço
        class Endereco {
            constructor(rua, numero, bairro, cidade, complemento) {
                this.rua = rua;
                this.numero = numero;
                this.bairro = bairro;
                this.cidade = cidade;
                this.complemento = complemento;
            }
        }

        // Classe Pessoa
        class Pessoa {
            constructor(nome, cpf, telefone, sexo, endereco) {
                this.nome = nome;
                this.cpf = cpf;
                this.telefone = telefone;
                this.sexo = sexo;
                this.endereco = endereco;
            }

            seApresentar() {
                return `Prazer, meu nome é ${this.nome}.`;
            }
        }

        // Classe Vendedor que herda de Pessoa
        class Vendedor extends Pessoa {
            constructor(nome, cpf, telefone, sexo, endereco) {
                super(nome, cpf, telefone, sexo, endereco);
            }
        }

        // Classe Cliente que herda de Pessoa
        class Cliente extends Pessoa {
            constructor(nome, cpf, telefone, sexo, endereco) {
                super(nome, cpf, telefone, sexo, endereco);
            }
        }

        // Criando endereços
        const endereco1 = new Endereco('Rua Alberto Mouffron', 92, 'Bairro JV', 'Cidade Valença', 'Complemento Antiga Toca do Coelho');
        const endereco2 = new Endereco('Rua B', 789, 'Bairro B', 'Cidade B', 'Complemento B');
        const endereco3 = new Endereco('Rua Piraquara', 593, 'Bairro Realengo', 'Cidade Rio de Janeiro', 'Complemento Condomínio PRP');

        // Criando pessoas
        const pessoa1 = new Pessoa('Vinícius do Valle (Pessoa)', '123.456.789-00', '(24) 3331-9694', 'Masculino', endereco1);
        const pessoa2 = new Vendedor('Maria Santos (Vendedora)', '987.654.321-00', '(11) 2452-9829', 'Feminino', endereco2);
        const pessoa3 = new Cliente('Filipe Batista (Cliente)', '456.789.123-00', '(21) 99201-3038', 'Masculino', endereco3);
       
        // Função para mostrar as pessoas na tela
        function mostrarPessoas() {
            const pessoas = [pessoa1, pessoa2, pessoa3];
            const pessoasDiv = document.getElementById('pessoas');
            pessoas.forEach(pessoa => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    <p>${pessoa.seApresentar()}</p>
                    <p><strong>CPF:</strong> ${pessoa.cpf}</p>
                    <p><strong>Telefone:</strong> ${pessoa.telefone}</p>
                    <p><strong>Sexo:</strong> ${pessoa.sexo}</p>
                    <p><strong>Endereço:</strong> ${pessoa.endereco.rua}, ${pessoa.endereco.numero} - ${pessoa.endereco.bairro}, ${pessoa.endereco.cidade}, ${pessoa.endereco.complemento}</p>
                `;
                pessoasDiv.appendChild(card);
            });
        }

        // Mostrar as pessoas ao carregar a página
        mostrarPessoas();
    </script>
</body>
</html>
