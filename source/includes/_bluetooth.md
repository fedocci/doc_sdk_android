# Bluetooth

Toda comunidação do Pinpad com SDK é feita por Blutooth.

## Parear pinpad

Primeiramente será necessario parear seu pinpad com o celular do cliente

## Listar pinpads

Uma vez que o pinpad foi pareado, ele será visível pelo SDK

```java
Integer pinpads_length = Paggi.getPinpadListSize();
if(pinpads_length  > 0) {
  for(int i = 0; i < pinpads_length; i++){
    PinpadObject pinpadObject = Paggi.getPinpadFromListAt(i);
  }
}
```
