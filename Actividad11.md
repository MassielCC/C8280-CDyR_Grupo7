## Actividad 11 : Conceptos de introducción a las redes

### Problema 4: Análisis y diseño de red Peer-to-Peer (P2P)

Escenario: Un startup tecnológico desea implementar una red P2P robusta para permitir el intercambio eficiente de recursos computacionales entre usuarios distribuidos geográficamente. Esta red debe ser capaz de manejar intercambios dinámicos de archivos, distribución de carga, y debe incorporar medidas de seguridad para prevenir accesos no autorizados.
Preguntas:

1. ¿Cómo se diferencia una red P2P de una red cliente-servidor en términos de diseño y cómo están conectados los dispositivos?

   En una red P2P, todos los dispositivos pueden ser tanto clientes como servidores al mismo tiempo. Esto significa que pueden compartir cosas directamente entre ellos sin necesitar un jefe central. Por otro lado, en una red cliente-servidor, los clientes necesitan conectarse a un servidor central para obtener lo que necesitan.

2. ¿Qué cosas usarías para permitir que los dispositivos en una red P2P se comuniquen y compartan archivos?
   
   Para compartir archivos, una buena opción es usar algo llamado BitTorrent, que es muy bueno para eso. Para comunicarse entre sí, los dispositivos necesitan seguir reglas llamadas protocolos, como TCP/IP. También es importante asegurarse de que la información esté protegida con encriptación para que no se pueda leer por cualquier persona.

3. ¿Qué problemas de seguridad podría haber en una red P2P y cómo los podríamos resolver?
   
   En una red P2P, podría haber problemas como cuando alguien trata de bloquearla para que nadie más pueda usarla, o cuando alguien trata de espiar lo que se está diciendo entre los dispositivos. También podría haber programas maliciosos tratando de meterse en la red. Para solucionar estos problemas, podemos usar cosas como cortafuegos para controlar el tráfico, y programas antivirus para detectar y eliminar los programas maliciosos.

4. ¿Cómo asegurarías que todos los dispositivos en una red P2P comparten la carga de trabajo de manera justa?
   
   Cuando tienes algunos dispositivos que están haciendo más trabajo que otros en una red P2P, puedes usar algoritmos especiales para asegurarte de que todos compartan la carga de trabajo por igual. También puedes usar trucos como guardar información temporalmente en diferentes dispositivos para que no se sature uno solo. De esta manera, todos los dispositivos pueden trabajar juntos de manera eficiente




import socket
import threading

class Peer:
    def __init__(self, host, port):
        self.host = host
        self.port = port
        self.peers = []
        self.server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.server.bind((self.host, self.port))
        self.server.listen(5)
        print(f"Nodo iniciado en {self.host}:{self.port}")
        threading.Thread(target=self.accept_connections).start()

    def accept_connections(self):
        while True:
            client, address = self.server.accept()
            print(f"Conectado con {address[0]}:{address[1]}")
            self.peers.append(client)
            threading.Thread(target=self.handle_client, args=(client,)).start()

    def handle_client(self, client):
        while True:
            try:
                data = client.recv(1024)
                if data:
                    print(f"Recibido: {data.decode()}")
                    self.broadcast_data(data, client)
            except Exception as e:
                print(f"Error: {e}")
                client.close()
                self.peers.remove(client)
                break

    def broadcast_data(self, data, sender):
        for peer in self.peers:
            if peer is not sender:
                peer.send(data)

    def send_message(self, message):
        encoded_message = message.encode()
        for peer in self.peers:
            peer.send(encoded_message)

    def connect_to_peer(self, host, port):
        client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        client.connect((host, port))
        self.peers.append(client)
        print(f"Conectado al par en {host}:{port}")

def start_peer():
    node = Peer('127.0.0.1', 600)

    while True:
        print("1. Conectar a un par")
        print("2. Enviar mensaje a todos los pares")
        print("3. Salir")
        choice = input("Ingrese su opción: ")

        if choice == '1':
            host = input("Ingrese la dirección IP del par: ")
            port = int(input("Ingrese el puerto del par: "))
            node.connect_to_peer(host, port)
        elif choice == '2':
            message = input("Ingrese el mensaje a enviar: ")
            node.send_message(message)
        elif choice == '3':
            break
        else:
            print("Opción no válida. Inténtelo de nuevo.")

start_peer()

