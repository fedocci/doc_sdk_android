# Download tabelas

Para sua Pinpad como transacionar diferentes bandeiras e emissores é necessario que SDK tenha feito downlaod das tabelas AID e CAPKS

```java
ApplicationCache applicationCache = new ApplicationCache(getApplicationContext());
if (applicationCache.checkIfHasTables() == false) {
    DownloadTablesProvider downloadTablesProvider = new DownloadTablesProvider(SUA_ACTIVITY_AQUI);
    downloadTablesProvider.setConnectionCallback(new PaggiCallbackInterface() {
        public void onSuccess() { };
        
        public void onError() { };
    });
    downloadTablesProvider.execute();
}
```
