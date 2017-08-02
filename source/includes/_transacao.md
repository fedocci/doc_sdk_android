# Transacionar

Transações débito ou crédito

Use ```PaggiTransaction``` para setar os dados da transação. 

Tipos de transação ```TypeOfTransactionEnum.CREDIT; TypeOfTransactionEnum.DEBIT```

O limite de parcelas são 12x. Sendo assim ```Paggi.getInstalment(position)``` retorna um ```Enum``` do número de parcelas.
position 0 para 1x ... position 11 para 12x.

```java
PaggiTransaction paggiTransaction = new PaggiTransaction();

paggiTransaction.setAmount(amount);
paggiTransaction.setInitiatorTransactionKey(descriptor);
TypeOfTransactionEnum typeTransaction = TypeOfTransactionEnum.CREDIT;
paggiTransaction.setTypeOfTransaction(typeTransaction);

if (typeTransaction == TypeOfTransactionEnum.CREDIT) {
    int position = spNumber_instalment.getSelectedItemPosition();
    paggiTransaction.setInstalmentTransactionEnum(Paggi.getInstalment(0));
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
                Log.i(TAG, "SUCCESS: " + transaction.toString());
            }
            @Override
            public void onError() {
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
            showCharges(charges);
        }
       @Override
        public void onError(Throwable throwable) {
            //erro ao cancelar transacão
           throwable.printStackTrace();
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

