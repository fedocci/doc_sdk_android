# Bluetooth

Toda comunicação do Pinpad com SDK é feita por Bluetooth.

## Parear pinpad

Primeiramente será necessário parear seu pinpad com o celular do cliente

## Listar pinpads pareados
(Uma vez que o pinpad foi pareado, ele será visível pelo SDK)

Esse método retorna uma lista com o nome de todos os dispositivos pareados. Use-a para popular um RecyclerView, Spinner ou outro componente visual que permite o usuario selecionar o pinpad desejado.

```java
ArrayList<String> listDevices = Paggi.getBondedDevices();
```

## Conetando um pinpad ao aplicativo

Use ```BluetoothConnectionProvider ``` para se conectar a um pinpad. Como parametro você devera passar o nome do pinpad que foi selecionado desde a lista de dispositivos pareados.


```java
        BluetoothConnectionProvider bluetoothConnectionProvider = new BluetoothConnectionProvider(pinpadSelected);
        bluetoothConnectionProvider.setConnectionCallback(new BluetoothCallback() {
            public void onSuccess(String manufactorName) {
                //Conexão realizada com sucesso, retorna o nome do dispositivo.
             }

            public void onError(String erroMessage) {
                //Falha ao se conectar, retorna uma mensagem de erro.
            }
        });
        bluetoothConnectionProvider.execute();
```

## Desconectando um pinpad

Para desconectar um dispositivo pinpad do aplicativo, use:
```java
Paggi.disconnectPinpad();
```


