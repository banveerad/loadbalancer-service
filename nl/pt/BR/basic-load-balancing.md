---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Balanceamento de carga básico
O serviço IBM Bluemix Load Balancer distribui tráfego entre múltiplas instâncias do servidor (bare metal e servidor virtual) que residem localmente, dentro do mesmo data center. 

## Balanceador de carga público 
Um nome completo do domínio publicamente acessível é designado à instância do serviço do balanceador de carga. É possível usar esse nome de domínio para acessar seus aplicativos hospedados atrás do serviço de balanceador de carga. As instâncias de cálculo de backend que hospedam seu aplicativo devem estar em uma rede privada do IBM Cloud. 

**NOTA:** como uma boa prática, recomenda-se provisionar seus servidores de backend como 'somente privados’, a menos que requeiram conectividade pública direta. Essa prática ajuda a alcançar melhor segurança, além de preservar o endereço IP público. Os aplicativos hospedados nesses servidores de backend continuam acessíveis na rede pública usando o balanceador de carga.  

## Portas/Protocolos dos aplicativos front-end e backend
É possível definir até dez portas (protocolos) do aplicativo front-end e mapeá-las para as respectivas portas (protocolos) nos servidores de aplicativos backend. O nome completo do domínio designado à instância do serviço do balanceador de carga e as portas do aplicativo front-end são expostos ao mundo externo. As solicitações recebidas de usuários são recebidas nessas portas. 

Por outro lado, as portas de backend são conhecidas apenas internamente. Essas portas de backend podem ou não ser as mesmas que as portas de front-end. Como exemplo, o balanceador de carga pode ser configurado para receber o tráfego web/HTTP recebido na porta de front-end 80, enquanto os servidores de backend estão atendendo na porta customizada 81. 

As portas/protocolos de front-end suportados são HTTP, HTTPS e TCP. As portas/protocolos de backend suportados são HTTP e TCP. O tráfego HTTPS recebido deve ser finalizado no balanceador de carga para permitir a comunicação HTTP de texto sem formatação com o servidor de backend. 

**NOTAS:**

* Durante a configuração inicial, é possível definir até duas portas de front-end apenas. Quando um balanceador de carga é criado, é possível editar a configuração de porta para definir portas adicionais, até o máximo de dez portas.
* As dez portas de front-end deverão ser mapeadas para o mesmo conjunto de instâncias do servidor de backend.
* O número máximo de instâncias do servidor que podem ser colocadas atrás de um balanceador de carga é 50.
* O intervalo de portas de 56.500 a 56.520 é reservado para propósitos de gerenciamento e não pode ser usado como portas virtuais de front-end. 

## Métodos de balanceamento de carga
Os três métodos de balanceamento de carga a seguir estão disponíveis para distribuir tráfego entre servidores de aplicativos backend:

* **Round-robin:** é o método de balanceamento de carga padrão. Com esse método, o balanceador de carga encaminha conexões do cliente recebidas no modo round-robin para os servidores de backend. Como resultado, todos os servidores de backend recebem praticamente um número igual de conexões do cliente.

* **Round-robin ponderado:** com esse método, o balanceador de carga encaminha conexões de cliente recebidas para os servidores de backend em proporção ao peso designado a esses servidores. A cada servidor é designado um peso padrão de 50, que pode ser customizado para qualquer valor entre 0 e 100. 

	Como exemplo, se houver três servidores de aplicativos A, B e C e seus pesos forem customizados para 60, 60 e 30, respectivamente, os servidores A e B receberão um número igual de conexões, enquanto o servidor C receberá metade desse número de conexões. 

	**NOTAS:** 

	* Reconfigurar o peso de um servidor para '0' significa que nenhuma nova conexão será encaminhada para esse servidor, mas qualquer tráfego existente continuará fluindo enquanto ele estiver ativo. Usar um peso de '0' pode ajudar a desativar um servidor normalmente e removê-lo da rotação de serviço. 
	* Os valores de ponderação do servidor são aplicáveis apenas com o método 'round-robin ponderado'. Eles são ignorados com os métodos de balanceamento de carga 'round-robin' e 'menos conexões'. 

* **Menos conexões:** com esse método, a instância do servidor que entrega o menor número de conexões em um determinado momento recebe a conexão do próximo cliente. 
