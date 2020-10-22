Proteger o dominio com validações.<br>
Expor comportamentos e esconder atributos.


###CDD - Cognitive Driven Development
###PCI - Ponto de Complexidade Intrinseca
    Branch                  (if/else/case/switch/for/while)   1 ponto cada. Tudo que tiver "{}"
    Tratamento Exception    (try/catch/finally)     1 ponto cada

Para api web considerar um limite de sete mais ou menos 2 pontos.
Caso a classe tenha atributos de dependencias (geralmente Controllers e Services), considerar sete pontos como limite.
Para classes com atributos de dados (geralmente Entities, Values Objects e Classes de entrada e saída de dados), podemos considerar nove o limite.



####Segue a sugestão de distribuição de carga intrínseca em função do contexto de uso de cada tipo de classe.

-Classes com atributos de dependência devem ter no máximo 7 pontos de complexidade.
 Alguns exemplos desses tipos de classes em um projeto:<br>
    -Controllers e Domain Services(services comumente usados) não devem passar de 7 pontos de carga intrínseca.<br>
     Elas lidam com fluxo de informações e isso deveria ser facilmente entendido.<br>
     Imagino que exista espaço inclusive para ser ainda mais restritivo.<br>
-Classes com atributos de dados, devem ter no máximo 9 pontos de complexidade. Temos alguns exemplos:<br>
    -Value objects. Elas em geral tem poucos métodos que operam sobre o estado.<br>
-Classes com estado persistente Essas classes geralmente são as entities.<br>
-Infrastructure Services podem ter a pontuação que você quiser. Elas geralmente são classes que acessam alguma coisa externa… Você quase não mexe e não tem problema gastar um pouco mais de tempo quando for dar manutenção.<br>
-Classes de configuração também podem ter a carga intrínseca que quiser… O template delas é montado uma vez e depois a manutenção acontece de vez em nunca.<br>
-Repository deve ter carga de no máximo 3 pontos. A depender do framework, seu repository pode até flertar com um ponto de carga intrínseca.<br>

####A primeira coisa que você deve pensar sobre o CDD é como adaptá-lo para seu cenário. Algumas sugestões:

    -Para classes que já existem aceite o fato da complexidade que já está lá.
     Pontue e coloque objetivos de refatoração para diminuir a complexidade de entendimento em termos percentuais relativos ao total já acumulado.
    -Para classes novas você pode estabelecer o limite restritivo;
    -Para manutenção, corretiva ou evolutiva, já leve em consideração o limite e construa os novos os códigos com o limite em mente;
###Importante:<br> 
É importante que você considere complexidade como um fator de compilação. 
Código com sintaxe errada não compila, a mesma coisa deveria acontecer para código que não respeita o limite de entendimento humano.

####Links importantes:

https://github.com/claudiooliveirazup/documentacao-cartao-branco/blob/master/informacao_suporte/error-object-oriented.md
https://github.com/luramarchanjozup/bootcamp-01-entendimentos

#####Controller:
Receber requisiçao, validar input, converter pra dominio, para poder validar as regras de negocio(service), e depois devolver a mensagem.

#####Regras de dominio no dominio:
Permitido desde que faça sentido.<br> 
Ex: se existe um dominio compra, faz sentido ter um calculo da compra dentro desse dominio.


#####Duvidas para proxima sessão:

#####TODO
- Validar o Markdown no cadastro de livros.
- Criar regex para isbn.
- Melhorar a utilização de getters and setters.


#####--------------------------------Atividade atual--------------------------------

##### - Finalizado.



####Problemas encontrados:
#####Durante implementação dos itens do pedido
-------------------------------------------X-------------------------------------------
- Bean property 'novoPedidoRequest.total' is not readable or has an invalid getter method: Does the return type of the getter match the parameter type of the setter?
- Faltava gettes e setters -.-

-------------------------------------------X-------------------------------------------<br>
Resolved [org.springframework.http.converter.HttpMessageNotReadableException: 
JSON parse error: 
Cannot deserialize instance of 
`java.util.ArrayList<br.com.bootcamp.zup.braz.rui.bootcamp01templatecasadocodigo.requests.NovoPedidoItemRequest>` 
out of START_OBJECT token; 
nested exception is com.fasterxml.jackson.databind.exc.MismatchedInputException: 
Cannot deserialize instance of 
`java.util.ArrayList<br.com.bootcamp.zup.braz.rui.bootcamp01templatecasadocodigo.requests.NovoPedidoItemRequest>` 
out of START_OBJECT token
 at [Source: (PushbackInputStream); line: 15, column: 17] 
 (through reference chain: br.com.bootcamp.zup.braz.rui.bootcamp01templatecasadocodigo.requests.NovaCompraRequest["novoPedidoRequest"]->br.com.bootcamp.zup.braz.rui.bootcamp01templatecasadocodigo.requests.NovoPedidoRequest["itens"])]

-Erro de sintaxe do JSON, eu estava montando sem passar um array, estava faltando os colchetes [].

-------------------------------------------X-------------------------------------------

###Config do projeto;
Language Level: 11 - Local variable syntax for lambda parameters <br>
Project SDK: Azul -11 java version "11.0.8"<br>
Banco: PostgresSQL 9.6


###Comandos importantes
-Verificar IP banco Docker<br>
docker network inspect dev_postgres-bootcamp01-network

-Reanalizar um projeto no SonarQube <br>
mvn sonar:sonar \
  -Dsonar.projectKey=bootcamp01 \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=5a99f16608b5b00898fb06ae91bdb58ac1358149
