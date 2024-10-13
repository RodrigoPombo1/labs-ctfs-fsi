### Wordpress CVE

Primeiro nós inspecionamos o site para tentar ver os plugins que usava e encontrámos esta página que nos diz que eles oferecem um serviço de wordpress hosting e em que especificam a versão do wordpress, os plugins e as versões de plugins que usam.

![image5](images_CTF3.md/image5.png)

Também encontrámos na secção de reviews deste serviço que havia um cliente insatisfeito por ter sido hackeado e que refere que o a razão teria sido por o serviço de hosting não estar com os plugins atualizados e a resposta do admin a dizer que não é verdade e que diz que são seguras porque na equipa dele há pessoas que estão a monitorizar isso.

![image7](images_CTF3.md/image7.png)

Logo decidimos ir investigar se o cliente tinha razão e se haviam vulnerabilidades com as versões dos plugins do serviço de hosting e se houvessem, como o próprio site em que ele está a vender estes serviços é de wordpress (conseguimos ver no html), ele é bem capaz de estar a usar as mesmas versões de plugins neste site que usa no seu serviço de hosting.

![image8](images_CTF3.md/image8.png)

Procurando por vulnerabilidades relativas à versão do wordpress e aos plugins acabámos por encontrar esta página de github [https://github.com/RandomRobbieBF/CVE-2023-2732](https://github.com/RandomRobbieBF/CVE-2023-2732) relativamente ao CVE-2023-2723 que pondo no site de CTF conseguimos confirmar que é a vulnerabilidade correta. Esta vulnerabilidade é referente ao plugin MStore API que no site usa a versão 3.9.0 e a vulnerabilidade aplica-se às versões inferiores ou iguais a 3.9.2.

![image9](images_CTF3.md/image9.png)

Nós em seguida não lemos corretamente o guia e simplesmente mudámos as últimas duas coisas que nos dizia para fazer para em vez de wordpress.lan ter 143.47.40.175:5001 e como o admin era o user 1 tal como no exemplo conseguimos.

![image1](images_CTF3.md/image1.png)

Mas mais tarde percebemos que era suposto termos executado um script de python como demonstrado no guia para ter uma lista dos utilizadores e ai perceber que o utilizador admin era o 1 e mudar o URL para o id 1.

![image3](images_CTF3.md/image3.png)

Ao ir ao URL [http://143.47.40.175:5001/wp-json/wp/v2/add-listing?id=1](http://143.47.40.175:5001/wp-json/wp/v2/add-listing?id=1) , obtemos que o browser nos diz que houve um erro ao redirecionar direito.

![image11](images_CTF3.md/image11.png)

E se voltarmos ao site normal, podemos ver que em cima temos a barra de administrador do site de wordpress:

![image10](images_CTF3.md/image10.png)

Carregamos no icon de wordpress no canto superior esquerdo:

![image4](images_CTF3.md/image4.png)

Vamos aos posts:

![image6](images_CTF3.md/image6.png)

E temos a flag que nos faltava na mensagem que o admin enviou aos seus empregados:

![image2](images_CTF3.md/image2.png)

Concluindo assim o CTF.

Resolver a vulnerabilidade:

Atualizar o plugin MStore API da versão 3.9.0 para a versão mais recente ou pelo menos para a versão 3.9.3.