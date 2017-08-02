# Download tabelas

Para sua Pinpad poder transacionar diferentes bandeiras e emissores é necessário que o SDK tenha feito o download das tabelas AID e CAPKS.

```java
ApplicationCache applicationCache = new ApplicationCache();
if (!applicationCache.checkIfHasTables()) {
    DownloadTablesProvider downloadTablesProvider = new DownloadTablesProvider();
    downloadTablesProvider.setConnectionCallback(new PaggiCallbackInterface() {
        public void onSuccess() {
            //tabelas baixadas
        };
        public void onError() {
           //erro ao baixar tabelas
        };
    });
    downloadTablesProvider.execute();
}else{
    //tabelas ja estão em cache
}
```
