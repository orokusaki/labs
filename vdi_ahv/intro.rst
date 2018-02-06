Introduction
------------

What is Desktop Virtualization?
+++++++++++++++++++++++++++++++

Desktop Virtualization, or Virtual Desktop Infrastructure (VDI), are terms used to describe a solution where a desktop Operating System (Windows 7, Windows 10, RHEL, etc.) runs as a Virtual Machine on top of a hypervisor in a datacenter. Users connect to the desktop from a client device through a brokering service. The desktop is presented via a remote display protocol, sending screen updates from the VM to the client and peripheral input from the client to the VM. VDI is also often used to generically describe other aspects of End User Computing (EUC), such as server based computing (SBC), user persona management, application virtualization, and operations monitoring. Other aspects of EUC that fall outside the umbrella of VDI include physical device management, software patch management, and mobile device management.

While there are many different motivations to implement a VDI solution, a common goal can be defined as: *Delivering a uniform desktop experience to any user in any location from any device.*

The goal of this workshop is to provide a functional understanding of the components of a Citrix XenDesktop solution, benefits, common challenges, solution design, and the role Nutanix plays in this important workload. In the lab exercises you will deploy a fully functional XenDesktop environment running on top of the Nutanix AHV hypervisor.

Why Desktop Virtualization?
+++++++++++++++++++++++++++

Why NOT Desktop Virtualization?
+++++++++++++++++++++++++++++++

.. enter Nutanix
.. enter AHV
.. resiliency

.. why not DaaS

Generic VDI Components
++++++++++++++++++++++

Remote Display Protocol - A protocol whose primary purpose is to display the screen of a computer from a host to a client over a network. The protocol may use TCP, UDP, or a combination of both. Common remoting protocols include VNC, Microsoft RDP, Teradici PCoIP, and Citrix HDX. Different protocols offer different sets of capabilities for delivering remote displays such as:

  * Ability to deliver a high fidelity experience over WAN conditions that may involve limited bandwidth and high latency
  * Support for USB devices connected to the client and remoted to the host
  * Client location based services like default printer selection
  * Native client support for multiple platforms (Windows, macOS, Linux, iOS, Android, etc.)
  * Client support for sessions delivered via HTML5

Evaluating the capabilities of the remoting protocol can be an important aspect of choosing a virtual desktop solution.

Client - The client can refer to either the device or software used to connect to the virtual desktop. It is responsible for providing a local display and inputs (Keyboard, Mouse, etc.) to and from the host using the remote display protocol. Client devices can be broken down into four categories:

  * Traditional devices - Desktops and laptops running client software are typically the most flexible end points for accessing a virtual desktop. It is common for personally owned laptops and desktops to be used to remotely access a corporate VDI environment. It is also common for net new virtual desktop deployments to continue to use existing desktops as a means of accessing virtual desktops. This can be beneficial as it offsets the capital cost of investing in VDI and, as minimal local compute is required to run the client software in many scenarios, older desktop models can continue to be used well past their traditional lifespan. The primary downside of using corporate desktops as VDI clients is the need to still patch and maintain those devices, which can detract from the operational benefits of implementing VDI.
  * Mobile devices - Devices such as smartphones and tablets are used both as personal devices for remote access as well as corporate owned devices where the mobile form factor is preferred for a particular use case but access to traditional desktop applications is required. Mobile client software can be limited in function compared to traditional devices or thin clients due to limitations of the mobile OS (e.g. limited peripheral support).
  * Thin Clients - Thin clients are purpose built devices available from a number of manufacturers including Dell, Lenovo, HPE, IGEL, and others. A thin client runs either an embedded Windows or Linux operating system with client software that may be customized by the OEM. Thin clients come in a variety of different hardware configurations to support use cases ranging from simple kiosks to high end graphics supporting 4+ monitors. Thin clients are typically "locked down" from the perspective that they only allow a user to access their virtual environment, preventing the execution of local workloads. Thin clients benefit from being simpler to patch and maintain, are low cost, have long product lifecycles, and have low power consumption. OEMs and other providers such as ThinKiosk offer software based solutions to re-purpose existing desktop hardware to maintain traditional desktops similarly to thin clients.
  * Zero Clients - Zero clients are stateless purpose built devices typically designed to work with a single virtual desktop solution. They may use dedicated proprietary hardware or a very small OS running on ARM or x86 processors and do not support the installation of third party software. While they may not support all features of a display protocol and new display protocol features may lag behind their client software counterparts, zero clients can be the simplest clients to deploy and maintain. They also have low costs, product lifecycles and low power consumption similar to thin clients.

Connection Broker - The Connection Broker is a backend infrastructure role that manages all hosted resources (virtual desktops, server desktops, server applications, physical machines), provides the controls necessary to define which users can connect to which resources, and assigning users to the defined resource at user logon. The broker integrates with authentication systems such as Active Directory and also with SSL VPNs to broker WAN connections. Resources are typically allocated by the broker in one of two ways:

  * Static/Dedicated - Static or Dedicated assignments involve a resource being permanently assigned to a specific user. This type of assignment is most commonly used for Persistent virtual desktops 
  * Random/Shared -

Web Portal - The Web Portal is a backend infrastructure role responsible for providing a front end experience for a user to authenticate to a remote environment. This may be in the form of a web page accessed via a browser or a native client connecting to a portal address. The portal may also be responsible for integration with authentication systems and SSL VPNs.

Provisioning - Provisioning refers to the creation of the virtual desktops or servers from a template virtual machine. The means of provisioning vary widely across different VDI solutions.

SSL VPN - An SSL VPN is a type of VPN that can be used by a standard web browser and unlike traditional VPNs does not require the installation of dedicated client software. Thie lightweight approach is ideal for flexible remote access to a VDI environment when the end user may not have the ability to install software on the client device. SSL VPNs also provide an inherently smaller attack vector for remote connections as you're not extending direct LAN access to a potentially untrusted client device. SSL VPNs can be implemented as physical appliances, purpose built virtual appliances, and as software that can be deployed on a traditional OS.

Desktop Types - A VDI environment can provide a mix of different hosted resource types to meet the needs of a wide range of use cases.

  * Persistent
  * Non-Persistent
  * Server Based Computing
    * Desktops
    * Apps
    .. why

Profile Management

Application Virtualization

Application Layering



Citrix XenDesktop Components
++++++++++++++++++++++++++++

Receiver

Desktop Delivery Controller

StoreFront

Provisioning Services

Machine Creation Services

NetScaler Gateway

UPM & WEM

Unidesk

Desktop Types
  static
  Pooled
  XenApp



Designing a VDI Solution
++++++++++++++++++++++++

.. resiliency?

Discovery
.........

Provisioning
............

Sizing
......

Further Reading
+++++++++++++++
