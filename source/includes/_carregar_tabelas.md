# Carregar tabelas

Após fazer download das tabelas e parear sua Pinpad, será necessário carregar as tabelas AID e CAPKS na sua Pinpad.

```java
LoadTablesProvider loadTablesProvider = new LoadTablesProvider(pinpadSelected);
loadTablesProvider.setConnectionCallback(new PaggiCallbackInterface() {
  public void onSuccess() {
    //tabelas carregadas
  };

  public void onError(Throwable throwable) {
    //erro ao carregar tabelas
  };
});
loadTablesProvider.execute();
```
