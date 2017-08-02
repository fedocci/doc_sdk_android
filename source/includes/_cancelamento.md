# Cancelar transação

Para cancelar uma transação, basta informar a id da mesma.

```java
ReversingTransactionProvider reversingTransactionProvider = new ReversingTransactionProvider(charge.getId());
reversingTransactionProvider.setConnectionCallback(new CancelTransactionCallback() {
    @Override
    public void onSuccess(Charge charge) {
        display("Cancelamento efetuado: "+charge.toString());
    }

    @Override
    public void onFailure(Throwable throwable) {
        display("Cancelamento não foi efetuado ");
        throwable.printStackTrace();
    }
});
reversingTransactionProvider.execute();
```
