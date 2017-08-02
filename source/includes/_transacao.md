# Transacionar

Transações débito ou crédito

Use ```PaggiTransaction``` para setar os dados da transação. 

Tipos de transação ```TypeOfTransactionEnum.CREDIT; TypeOfTransactionEnum.DEBIT```

O limite de parcelas são 12x. Sendo assim ```Paggi.getInstalment(instalmentNumber)``` retorna um ```Enum``` do número de parcelas.
1 para 1x, 2 para 2x ... 12 para 12x.

```java
PaggiTransaction paggiTransaction = new PaggiTransaction();

paggiTransaction.setAmount(amount);
paggiTransaction.setInitiatorTransactionKey(descriptor);
TypeOfTransactionEnum typeTransaction = TypeOfTransactionEnum.CREDIT;
paggiTransaction.setTypeOfTransaction(typeTransaction);

if (typeTransaction == TypeOfTransactionEnum.CREDIT) {
    paggiTransaction.setInstalmentTransactionEnum(Paggi.getInstalment(8));
} else {
    paggiTransaction.setInstalmentTransactionEnum(InstalmentTransactionEnum.ONE_INSTALMENT);
}
```

Após setar os dados da transação, use ```TransactionProvider``` para iniciar o processo.
```java
TransactionProvider provider = new TransactionProvider(paggiTransaction);
provider.setConnectionCallback(new TransactionCallback() {
            @Override
            public void onSuccess(Transaction transaction) {
                //transaçao realizada
            }
            @Override
            public void onError() {
                //erro ao transacionar
            }
        });
provider.execute();
```

# Listar transações

A listagem de transações é feito pela chamada de ```ChargesProvider```

```java
ChargesProvider provider = new ChargesProvider();
provider.setConnectionCallback(new ChargesCallback() {
       @Override
        public void onSuccess(ArrayList<Charge> charges) {
            //retorna uma lista de transações
        }
       @Override
        public void onError(Throwable throwable) {
            //erro ao lista transações
        }
});
provider.execute();
```

# Cancelar transação

Para cancelar uma transação, basta informar a id da mesma.

```java
ReversingTransactionProvider reversingTransactionProvider = new ReversingTransactionProvider(charge.getId());
reversingTransactionProvider.setConnectionCallback(new CancelTransactionCallback() {
    @Override
    public void onSuccess(Charge charge) {
        //retorna a transaçao cancelada
    }

    @Override
    public void onFailure(Throwable throwable) {
        //erro ao cancelar transaçao
    }
});
reversingTransactionProvider.execute();
```

