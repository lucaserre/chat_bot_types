# Chat Bots Types (Introdução)

Serviços de núvem, LLMs, APIs. Esses são os principais recursos utilizados atualmente por diversas áreas da tecnologia, indo do front-end ao back-end. 
Assim, como forma de praticar e me aprofundar em conteúdos atuais da faculdade, decidi que, além de estudar sobre a história da IA e matemática computacional, também era necessário compreender sobre conceitos atuais. 
Através disso, percebo que existe muitas ferramentas são muito antigas, mas também, atuais, e as novas formas vieram para aprimorar o que já existia. 

Nesse contexto, é importante salientar o quanto grandes empresas disponibilizam conteúdo e recursos para estudantes, os quais me viabilizaram realizar tais atividades. 
Plataformas como AWS, Twilio e Ngrok foram muito importantes e fizeram com que, além dos dolares e produtos gratuitos, disponibilizaram treinamentos e documentações, as quais você pode ler e praticar da melhor maneira possível.
O que se iniciou como uma simples unidade da faculdade, terminou com uma sensação de dever cumprido e com conhecimento ainda mais alerta sobre o que preciso de fato estudar. 



## Primeiros Passos (Telegram + Python)

  Uma atividade de extensão da faculdade me fez criar uma solução para resolução de problemas ambientais em uma comunidade específica, tendo como base meu curso atual (Ciência da Computação) e utilizando soluções que visavam
desenvolvimento e novas tecnologias. Pensei em diversos projetos, mas o que me despertou um interesse genuíno foi um chat-bot, que receberia denúncia do que poderia ter de errado na comunidade específica, os quais tive que de-
finir o que seria o foco. Através de um questionário consegui definir que o local possui 3 probleams específicos: buracos nas ruas (que demoravam para serem resolvidos), descarte incorreto de lixo (lixeiras lotadas) e de som (motos, vizinhos barulhentos), 
sendo definido do com mais reclamações, para o com menos reclamações.  

Posteriormente fiz outra pesquisa para verificar como esses problemas afetavam e como ele eram tratados pela comunidade, além de também verificar se as pessoas estariam de acordo com uma pissível solução. A seguir uma foto dos resultados: 

<img width="771" height="699" alt="image" src="https://github.com/user-attachments/assets/66f2a79c-e29b-4c3a-91bc-46441fa6e7ae" /> 
<img width="775" height="698" alt="image" src="https://github.com/user-attachments/assets/53f5e98a-7865-4d8a-8060-faddd6e171dc" />
<img width="782" height="371" alt="image" src="https://github.com/user-attachments/assets/d17d3768-19d7-47b4-9146-0ceed0bda763" />


Para ser algo gratuito e de uso para a própria comunidade, busquei soluções que não exigiam pagar por serviços. Assim, cheguei no telegram, que disponibiliza a criação de um bot, o qual só precisaremos configurar. Além disso, outras ferramentas 
como Ngrok e bibliotecas do Python (SQLite e Flask)

Tendo como produto final, o seguinte assistente: 

<img width="1848" height="1006" alt="image" src="https://github.com/user-attachments/assets/fc2f0404-3edb-47ff-be93-22e1f96e5a54" />
<img width="1853" height="1006" alt="image" src="https://github.com/user-attachments/assets/f69f4ccc-497f-4958-9e4b-6b4bd8161d36" />
<img width="1854" height="1007" alt="image" src="https://github.com/user-attachments/assets/cb1986fb-0271-4951-bff1-dd0637837d28" />


## Segunda Parte (Whatsapp + Python)

  Nesse momento foi onde enxerguei do potencial que seria isso dentro de uma organização maior, como seriam as regras de negócio, todos os algoritmos, e toda a engenharia de software em si. Mas, obviamente, teria que ser dentro de um dos app3
de conversa mais utilizado no País: o Whatsapp.

Para isso ocorrer, seria necessário utilizar créditos na Twilio, por exemplo. Porém, a plataforma para utilizar a API do Whatsapp e dentro da sua Sandbox, eles disponibilizam um pequeno valor, de maneira que você consiga realizar testes. Utilizando-me
desse auxilio, pensei que a lógica era minha única barreira agora, visto que um chatbot precisa atender a clientes que podem responder de diversas maneiras possíveis, mandando mensagens sem contexto, áudios e até imagens. Assim, deveria ter uma maneira de 
organizar o que era recebido para limpar, que dentro da programação temos um termo chamado *Sanitization*, que tem como objetivo transformar as mensagens escritas em um formato, para outro que o meu script conseguirá ler. Então, o cliente poderia digitar
o CPF dele com pontos e barras, que ele sempre chegaria limpo (ex:11122233344)

## Terceiro Momento (Whatsapp + Python + AWS)

  Por fim, quis trazer para um momento atual, onde a inteligência artifical está sendo aplicada em diversos setores das empresas, seja financeiro, para atendimento ao cliente com informações sobre sua conta, seja sobre processos de pagamento dentro de uma empresa,
  como contas a pagar, contas a receber, documentação, etc. 

  Como sempre, existe a necessidade de realizar pagamentos de alguns serviços, mas, como bom estudante, sempre obtenho meus recursos iniciais gratuitos, tendo a Amazon disponibilizado $200.00 para utilizar, o qual apliquei em serviços como Bedrock (IA) e Lambda (Servidor 24h).
Esse não foi necessário criar uma lógica tão grande, ou tão além do produto anterior, somente a criação de algo chamado *System Prompt*, o que determinará o que a IA deverá fazer, como ela deve agir dentro das respectivas mensagens que receber, etc. Dessa forma, seria necessário
Criar regras que não permitissem ao usuário conversar com o chat como se fosse uma IA qualquer e ter acesso a todos os tipos de informações. Além de regras para finalizar o chat e apagar dados dentro do dicionário temporário criado. 

'''
    System Prompt
  
    system_prompt = f"""Você é um assistente administrativo, responsável pelo setor financeiro da empresa x. Você possui informações como valor de parcelas (com e sem juros), quantidade de parcelas em aberto, valor individual de cada parcela, quantos pontos o cliente possui, emissão de           boletos, e cobrança.

    Você deve atender a todos os clientes de maneira cordial, mesmo que te chamem/respondam com gírias, prezando por respostas pragmáticas e que não fujam do escopo o qual você é responsável, ou seja, parte financeira.
    
    Além disso, também e zeloso pela segurança de informações que, apesar da pessoa estar validada, ou na base de dados, ela não tem nem pode ter acesso a informaçoes de outros clientes além do CPF o cadastrado para o contrato específico.
    
    Você deve realizar uma analise contudente de como o cliente está respondendo, pontuando entre muito bravo, bravo, chateado, desconfortável, de acordo, feliz, e responder com base nesse sentimento dele, sendo que , caso esteja entre muito bravo e desconfortável,, você de utilizar palavras as quais respostas tranquilizarão os respectivos clientes.
    
    A regra de desconto se baseará na forma e na data a qual o cliente realizará o pagamento. Se houver somente uma parcela com até 3 dias de atraso, se o cliente solicitar, você pode retirar os juros e multa por atraso para pagamentos através do PIX, caso contrário, mantenha. Caso ultrapasse os 3 dias ou tenha duas ou mais parcelas em atraso, não é permitido a retirada dos juros, sendo necessário um atendimento humano para negociação, a qual você perguntará ao cliente se deseja ser atendido para verificar a possibilidade de isenção dos juros. 
    
    Sempre pergunte se o cliente precisa de mais alguma ajuda. Caso ele indique que o atendimento pode ser encerrado, despeça-se educadamente e adicione OBRIGATORIAMENTE a palavra-chave [FIM_ATENDIMENTO] no final da sua resposta. Dados do cliente:{json.dumps(info_cliente, ensure_ascii=False)} """



'''

A seguir o resultado: 

<img width="1278" height="909" alt="image" src="https://github.com/user-attachments/assets/d346aff3-7b8a-43f6-95df-cd1388c26521" />
<img width="1282" height="911" alt="image" src="https://github.com/user-attachments/assets/199c1736-11d4-4d8d-b29e-884df36910f8" />
<img width="1274" height="266" alt="image" src="https://github.com/user-attachments/assets/f1382a18-5a7f-4aa2-b243-7743de8246ed" />






