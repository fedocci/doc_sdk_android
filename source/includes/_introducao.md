# Introdução

## Bem-vindo

Bem-vindo a documentação do Paggi SDK Android, aqui você irá encontrar informações para integrar seu app (Android) com nosso SDK para poder transacionar com nossa MPOS.

Para ter mais informações sobre o Paggi, entre em nosso [site](https://www.paggi.com).

Qualquer dúvida pode entrar em contato pelo email: `contato at paggi.com` .

## Por onde começar

Comece baixando a última versão do nosso SDK em seu [repositório](https://github.com/kiik-payments/doc_sdk_android/releases/latest).

## Configuração

Para configurar nosso SDK é preciso passar como argumento seu `MAIN_ACTIVITY`, `USER`, `TOKEN`, que está em nosso [dashboard](https://pos.paggi.com) e o ambiente (que por padrão é `Environment.PRODUCTION`

```java
Paggi.init(context, user_id, code, Environment.STAGING);
```

O SDK dispões de dois ambientes.
```java
Environment.PRODUCTION
Environment.STAGING
```

O SDK requer quealgumas permissoes de usuarios sejam adicionadas no arquivo Manifest.
```xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
```
