# Carregar tabelas

Após fazer download das tabelas e parear sua Pinpad, será necessario carregar as tabelas AID e CAPKS na sua Pinpad.

```java
LoadTablesProvider loadTablesProvider = new LoadTablesProvider(this, new GcrRequestCommand(), pinpadSelected);
loadTablesProvider.setConnectionCallback(new PaggiCallbackInterface() {
  public void onSuccess() { };

  public void onError() { };
});
loadTablesProvider.execute();
```
