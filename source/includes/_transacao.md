# Transacionar

Depois de carregar as tabelas na Pinpad, será possível transacionar no débito ou crédito


```java
PaggiTransaction paggiTransaction = new PaggiTransaction();
paggiTransaction.setAmount("10,00"); // Valor será em String 
paggiTransaction.setInitiatorTransactionKey("Paggi descricao"); // Descrição que será mostrada na fatura
paggiTransaction.setInstalmentTransactionEnum(InstalmentTransactionEnum.ONE_INSTALMENT); // Número de parcelas
paggiTransaction.setTypeOfTransaction(TypeOfTransactionEnum.CREDIT);

// Em seguida é preciso enviar para o Paggi a transação

TransactionProvider provider = new TransactionProvider(ACTIVITY_ATUAL, paggiTransaction);
provider.setConnectionCallback(new PaggiCallbackInterface() {
  public void onSucess() { };
  public void OnError() { };
});
```
