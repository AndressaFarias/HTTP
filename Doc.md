* O DNS realiza a tradução do nome de um domínio para o endereço de IP. Existem vários servidores DNS no mundo e é fundamental para a nossa web o funcionamento deles.

* Vários protocolos definem a sua porta padrão como por exemplo o FTP que usa 21 ou SSH que usa 22.

#  URI ou URL?

Muitas vezes, desenvolvedores usam a sigla URI (Uniform Resource Identifier) quando falam de endereços na web. Alguns preferem URL (Uniform Resource Locator), e alguns misturam as duas siglas à vontade. Há uma certa confusão no mercado a respeito e mesmo desenvolvedores experientes não sabem explicar a diferença. Então, qual é a diferença?

Resposta 1 (fácil): Uma URL é uma URI. No contexto do desenvolvimento web, ambas as siglas são válidas para falar de endereços na web. As siglas são praticamente sinônimos e são utilizadas dessa forma.


Resposta 2 (mais elaborada): Uma URL é uma URI, mas nem todas as URI's são URL's! Existem URI's que identificam um recurso sem definir o endereço, nem o protocolo. Em outras palavras, uma URL representa uma identificação de um recurso (URI) através do endereço, mas nem todas as identificações são URL's.

URL são os endereços da Web
Uma URL começa com o protocolo (por exemplo https://) seguido pelo domínio (www.alura.com.br)
Depois do domínio pode vir a porta, se não for definida é utilizada a porta padrão desse protocolo
Após o domínio:porta, é especificado o caminho para um recurso (/course/introducao-html-css)
Um recurso é algo concreto na aplicação que queremos acessar


* HTTP segue o modelo REQUEST- RESPONSE

* Uma requisição sempre deve ser enviada com todas as informações necessárias, o que faz uma requisição ser sempre independente das demais.

* Uma sessão HTTP nada mais é que um tempo que o cliente permanece ativo no sistema! 

# Cookie

Quando falamos de Cookies na verdade queremos dizer Cookies HTTP ou Cookie web. Um cookie é um pequeno arquivo de texto, normalmente criado pela aplicação web, para guardar algumas informações sobre usuário no navegador.

Quais são essas informações depende um pouco da aplicação. 

* Quando enviamos uma requisição HTTP, todos os dados para que ela seja respondida devem ser enviados. Mas e o e-mail e a senha? Quando o login é feito, a Alura tem certeza de que um usuário existe e gera uma identificação quase aleatória pra esse usuário, lembra? E esse número fica salvo em um arquivo especial, chamado cookie, que é gerado e enviado por cada site :)


O protocolo HTTP segue o modelo Requisição-Resposta
Sempre o cliente inicia a comunicação
Uma requisição precisa ter todas as informações para o servidor gerar a resposta
HTTP é stateless, não mantém informações entre requisições
As plataformas de desenvolvimento usam sessões para guardar informações entre requisições




# Depurando o método HTTP

Lembrando que o método define a ação ou intenção da requisição HTTP (GET é igual a receber). 

O código da resposta dá uma dica ao cliente se a requisição foi um sucesso ou não, e qual foi o problema em caso de falha. 

Na documentação oficial, se diz a respeito da classe de códigos que começam com 2xx:

2xx - Resposta bem sucedida!COPIAR CÓDIGO
Essa classe de códigos de status indica que a ação solicitada pelo cliente foi recebida, compreendida, aceita e processada com êxito.

A tabela completa de mensagens HTTP pode ser vista em: https://www.w3schools.com/tags/ref_httpmessages.asp.


A classe 5xx significa que houve algum problema no servidor.

Por exemplo: 500 - Internal Server Error, ou outro famoso: 503 - Service Unavailable.

O código 500 acontece com frequência quando estamos desenvolvendo uma aplicação web e, ao testar, percebemos que erramos algo na lógica que gerou um problema no servidor.



404 é o código clássico que indica que o recurso não foi encontrado. Em geral, a classe 4xx indica que o cliente errou algo na requisição.

Segue um outro exemplo da classe 4xx, tente acessar: https://s3.amazonaws.com/caelum-online-public/http/qq.png

Nesse caso o código de resposta é 403(não permitido): o cliente não tem a permissão.



Quando enviamos parâmetros na URL, devemos iniciar pelo ?, o nome do parâmetro e um =, para separar o nome do parâmetro do seu valor:

?nome_do_parametro=seu_valorCOPIAR CÓDIGO
Quando usamos mais do que, um parâmetro devemos usar & para separá-los:

?nome_do_parametro=seu_valor&nome_do_outro_param=valor



GET é normalmente usado para pesquisas, mas isso depende um pouco de como a plataforma e o desenvolvedor usam esse método. Na vida real, vocês vão encontrar muitos exemplos que usam requisições do tipo GET, não só para pesquisas.

O protocolo HTTP define que o GET deve ser utilizado apenas para acessar os dados, mas HTTP, como protocolo, não pode impedir o desenvolvedor de fazer algo diferente. Por exemplo, veja a requisição a seguir:


 O método POST deixa os parâmetros no corpo da requisição, assim evita que informações importantes, como a senha, fiquem explícitas na URL.


 # Web Service

 * Um Web Service disponibiliza uma funcionalidade na web, através do protocolo HTTP;

 * A grande diferença de um Web Service é que os dados não vem no formato HTML, e sim em algum formato independente da visualização, como XML ou JSON;

  # Serviços Web -REST

  REST é um padrão arquitetural para comunicações entre aplicações
Ele aproveita a estrutura do HTTP
Recursos são definidos via URI
Operações com métodos HTTP(GET/POST/PUT/DELETE)
Cabeçalhos(Accept/Content-Type) são usados para especificar as representações(JSON,XML,...)


Em alguns cabeçalhos do HTTP devemos especificar algum formato. Os formatos são chamados na documentação de MIME types. E na definição do cabeçalho usamos a seguinte estrutura: tipo/subtipo. São tipos conhecidos:


`text, image, application, audio e video`


E alguns subtipos:
text -> text/plain, text/html, text/css, text/javascript

image -> image/gif, image/png, image/jpeg


audio -> audio/midi, audio/mpeg, audio/webm, audio/ogg, audio/wav

video -> video/mp4

application -> application/xml,  application/pdf

Para conhecer outros formatos aceitos você pode acessar aqui: https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types


* a tecnologia HPACK é especialista em comprimir os Headers da requisições/respostas HTTP, deixando as mais leves.


# HTTP 2

Quando estamos utilizando Headers Stateful, simplesmente colocamos nas requisições os cabeçalhos que se alteraram entre uma e outra, trazendo uma enorme economia de dados, visto que toda requisição HTTP possui um cabeçalho e que, muitas vezes, no HTTP/1.1, cabeçalhos repetidos eram trafegados em todas as requisições.

---

Neste capítulo, o que aprendemos? Vimos que o HTTP2 atua sobre o que já conhecemos do HTTP. Ou seja, ele não muda nada em relação ao que já conhecemos de HTTP. E que todo o seu conteúdo é usado no HTTP2 de forma bastante simples.

Hoje, o que o HTTP2 especifica é mais a nível de servidor. E acaba que nós desenvolvedores não atuamos tanto nesse nível. Fica mais na outra ponta, que é quem vai produzir servidores e tudo mais, seguir esse novo protocolo.

Vimos que HTTP2 é nada mais que o HTTP com algumas melhorias, até porque o HTTP1 estava bastante desatualizado em relação ao que o mercado já vinha sofrendo.

Também vimos que os headers são binários e eles são comprimidos com algoritmos chamados de HPACK.

Vimos ainda, que o HTTP2 habilita o GZIP como padrão na resposta, logo, esses dados vêm zipado. Coisa que tínhamos que configurar manualmente na versão anterior, ou seja, HTTP1.1.

Além disso, no HTTP2, as requisições e respostas podem ser paralelas. Não precisamos ficar esperando que uma requisição termine pra fazer a próxima. Temos uma otimização maior.

Outro assunto foi que os cabeçalhos guardam status. Quando enviamos uma requisição, a próxima, para o mesmo domínio, não precisa enviar os mesmo dados que já foram trafegados na última. Conclui-se que no HTTP2 isso é evitado, ou seja, menos informação enviada, menos dados que enviamos, menos banda que usamos do usuário, mais feliz ele fica.

Além de Headers Stateful, vimos também que o HTTP2 especifica o famoso Server-push, que é o ato do servidor enviar dados sem que o browser tenha pedido, que foi o que aconteceu lá no index.html. O HTTP2 pode enviar dados diretamente para o browser sem ficar esperando uma requisição. Assim, ele dá um passo além.