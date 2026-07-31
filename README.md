# HamburgueriaZ 🍔📱

Este repositório contém a documentação técnica e arquitetura do aplicativo mobile nativo **HamburgueriaZ**, desenvolvido como projeto prático para a disciplina de Desenvolvimento Mobile na graduação de Análise e Desenvolvimento de Sistemas.

O objetivo do projeto foi criar uma solução prática em que os usuários pudessem customizar seus pedidos de hambúrgueres diretamente pelo smartphone, calculando o valor final de forma dinâmica e integrando recursos nativos do sistema Android.

> 📂 **O relatório técnico completo em formato PDF está disponível neste repositório!**

---

## 🛠️ Especificações Técnicas e Arquitetura

O desenvolvimento foi fundamentado na separação clara entre a interface visual (XML) e a lógica de negócios (Java):

* **Ambiente de Desenvolvimento:** Android Studio (API 23 - Android 6.0 Marshmallow, garantindo ampla compatibilidade).
* **Linguagem de Programação:** Java.
* **Interface do Usuário (UI):** Desenvolvida em XML utilizando componentes nativos como `EditText` (nome do cliente), `CheckBox` (adicionais), botões de incremento/decremento de quantidade e `ImageView`.
* **Padronização Visual:** Implementação de estilo reutilizável centralizado no arquivo `themes.xml` (denominado `EstiloTexto`) para garantir consistência visual em toda a interface.

---

## ⚙️ Regras de Negócio e Funcionalidades

### 1. Cálculo Dinâmico do Pedido
O aplicativo faz a gestão de estado em tempo real para somar os adicionais selecionados à quantidade de hambúrgueres desejada. A lógica de cálculo foi estruturada com base na seguinte tabela de valores:

| Item | Valor Unitário |
| :--- | :---: |
| Hambúrguer Base | R$ 20,00 |
| Adicional de Bacon | R$ 2,00 |
| Adicional de Queijo | R$ 2,00 |
| Adicional de Onion Rings | R$ 3,00 |

* **Validação de Quantidade:** Funções que atualizam o visor de quantidade, impedindo números negativos para garantir a integridade dos dados.

### 2. Comunicação Inter-App via Android Intents
Para evitar a necessidade de um servidor de e-mail próprio, o aplicativo utiliza a interoperabilidade do sistema Android:
* Ao clicar em "Fazer Pedido", é disparado um objeto **Intent** do tipo `ACTION_SENDTO`.
* Esse gatilho invoca o aplicativo de e-mail padrão do smartphone, preenchendo o assunto e estruturando o corpo do texto automaticamente com o resumo detalhado e os adicionais do pedido.

---

## 📈 Resultados Obtidos
Durante os testes em ambiente de emulação, a aplicação validou com sucesso:
* O cálculo perfeito de múltiplos itens (ex: 2 hambúrgueres com bacon e queijo resultando em R$ 48,00).
* A formatação correta do resumo estruturado.
* A abertura fluida do aplicativo de e-mail externo transportando os dados gerados.
