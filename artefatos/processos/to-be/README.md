# Processos TO-BE

## Processo 1: Catalogação e Organização de Livros

![processo-1](assets/Processo%201%20-%20Catalogação%20e%20Organização%20de%20Livros.png)

1. O atendente recebe um novo livro para catalogação na biblioteca.
2. O atendente insere o código ISBN do livro em um campo no sistema de gerenciamento de biblioteca.
3. O sistema verifica se já existe um livro cadastrado no banco de dados com esse código.
4. Caso exista, o sistema preenche os campos automaticamente com as informações existentes no banco de dados relacionadas ao livro.
5. Caso não exista um livro com esse código, o atendente deve preencher as informações relacionadas ao livro.
6. As informações do livro são automaticamente integradas ao sistema de gerenciamento de biblioteca.
7. O sistema fornece instruções sobre o setor onde o livro deve ser colocado nas estantes.
8. O atendente segue as instruções do sistema, colocando o livro no local designado.
9. O livro agora está catalogado e disponível para os usuários da biblioteca.

A implementação do processo de catalogação e organização de livros fornece uma mudança significativa na eficiência e precisão das operações na biblioteca. Agora quando um novo livro é recebido para catalogação, ao inserir o código ISBN do livro no sistema, é verificado se já existe um livro registrado no sistema com o mesmo código, caso exista, as informações referentes a esse livro são preenchidas automaticamente, reduzindo a necessidade de inserção manual de dados, o que diminui a possibilidade de erros e acelera o processo.

### Processo 1: Potencialidades e oportunidades de melhoria

- Integrar cadastro de novos livros com "lista de desejos" dos clientes: ter um sistema que envie uma notificação (e-mail ou SMS) aos clientes quando um livro que eles tenham cadastrado que gostariam de ler esteja disponível na biblioteca.

## Processo 2: Empréstimo de livros

![processo-2](assets/Processo%202%20-%20Empréstimo%20de%20livros.png)

1. A atendente acessa o sistema.
2. Solicita o cartão de cadastro do cliente.
3. Insere os dados do cartão no sistema.
4. A atendente realiza uma pesquisa no sistema para encontrar o livro desejado pelo cliente.
5. O sistema informa a disponibilidade do livro para a atendente.
6. O sistema fornece informações detalhadas sobre a localização do livro na biblioteca, auxiliando a atendente na busca pelo exemplar.
7. A atendente registra o empréstimo do livro no sistema, atualizando o status do item.
8. A atendente entrega o livro ao usuário, concluindo o processo de atendimento.

Com a implementação do sistema de empréstimo de livros, a biblioteca conta com uma melhoria contínua dos serviços oferecidos aos seus usuários. Este avanço não só simplifica o processo de empréstimo, mas também eleva a qualidade da experiência do usuário, proporcionando uma interação mais ágil e eficaz.

O atendente agora consegue rapidamente localizar e verificar as informações necessárias no sistema, como a disponibilidade e localização do livro. Além disso, pode automaticamente registrar o empréstimo do livro, atualizando o status do item e do cliente em tempo real.

Essa automação do processo de empréstimo agiliza o atendimento ao cliente, e reduz os erros associados à entrada manual de dados. Não há mais necessidade de procurar manualmente em planilhas físicas, garantindo melhor precisão do processo.

### Processo 2: Potencialidades e oportunidades de melhoria

- Alerta de pendências de empréstimos: integrar o sistema para que o atendente seja automaticamente informado sobre quaisquer pendências de empréstimos ou multas quando estiver realizando um novo empréstimo para o cliente. Isso permite uma abordagem proativa para resolver pendências e melhora a eficiência do processo de empréstimo.

- Implementar sistemas de autoatendimento: introduzir estações de autoatendimento na biblioteca, permitindo que os usuários realizem empréstimos de forma autônoma. Isso reduziria as filas e proporcionaria uma experiência mais rápida e conveniente para os usuários.

## Processo 3: Devolução de livros

![process-3](assets/Processo%203%20-%20Devolução%20de%20livros.png)

1. O cliente se dirige ao balcão de devoluções da biblioteca.
2. O cliente entrega o livro que deseja devolver ao atendente.
3. O atendente utiliza o ISBN para identificar o livro com empréstimo no sistema.
4. O sistema informa se há ou não multa a ser paga devido a atraso.
5. O atendente cobra o valor referente ao atraso informado pelo sistema.
6. O sistema atualiza o status do livro devolvido para ‘disponível’.
7. A devolução é confirmada.

A implementação do sistema resulta em uma eficiência significativamente maior no processo de devolução de livros. Entre os benefícios observados, destacam-se a redução de erros e perdas de livros, garantindo uma gestão mais precisa e eficaz do acervo. Além disso, o sistema proporciona uma atualização em tempo real da disponibilidade dos títulos, oferecendo aos usuários uma experiência mais ágil e satisfatória ao buscar e devolver livros.

No entanto, a solução de devolução atual possui suas limitações, uma vez que se restringe à entrega física do livro a um atendente. Além disso, o sistema não oferece notificações automáticas sobre as devoluções concluídas, exigindo verificações frequentes na pilha de livros devolvidos para confirmar o retorno dos exemplares.

### Processo 3: Potencialidades e oportunidades de melhoria

- Devolução sem interação humana: o próprio cliente pode devolver o livro emprestado por meio de uma área de autoatendimento onde é possível localizar pelo ISBN o livro e depositar o livro em um compartimento seguro.

- Notificação de entrega: ao ser concluída uma devolução o sistema irá notificar que há um exemplar para ser organizado juntamente com a sua posição facilitando a organização na hora de colocar o livro novamente na prateleira para uma nova locação.

- Necessidade de manutenção: no momento da devolução o atendente, após uma inspeção, pode sinalizar se há alguma necessidade de manutenção no exemplar devolvido.

- Multa por mau uso: no processo de devolução o atendente além de poder sinalizar que houve mau uso do livro, ele pode ou não gerar uma multa referente.
