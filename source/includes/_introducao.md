# Introdução

## Bem-vindo

Bem-vindo a documentação do Paggi SDK Android, aqui você irá encontrar informação de como integrar seu app (Android) com nosso SDK para poder transacionar com nossa MPOS.

Para ter mais informação sobre o Paggi, entre em nosso [site](https://www.paggi.com).

Qualquer dúvida pode entrar em contato pelo email: `contato at paggi.com` .

## Por onde começar

Começe baixando a última versão do nosso SDK em seu [repositório](https://github.com/kiik-payments/doc_sdk_android/releases/latest).

Após adicionar nosso jar em seu aplicativo, você também precisara adicionar as seguintes dependencies:

- json.jar

## Configuração

Para configurar nosso SDK é preciso passar como argumento seu `MAIN_ACTIVITY` e `TOKEN`, que está em nosso [dashboard](https://pos.paggi.com).

```java
PaggiStart.init(MAIN_ACTIVITY, TOKEN_PAGGI)
```
