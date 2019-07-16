---
title: Конфигурация сети устройства - Analytics Platform System | Документация Майкрософт
description: Analytics Platform System (APS) модуль создания и настройки с набором исправления IP-адресов на протяжении всех серверов и соответствующих устройств из Независимых заводском цеху. При доставке для этого модуля необходимо изменить конфигурацию IP-адрес внешнего (Ethernet) обращаться в соответствии с требованиями центра данных конкретного клиента.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9bc836e3e05525b18ea994e768f65012e5c3d945
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961473"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Конфигурация сети устройства для Analytics Platform System
Analytics Platform System (APS) модуль создания и настройки с набором исправления IP-адресов на протяжении всех серверов и соответствующих устройств из Независимых заводском цеху. При доставке для этого модуля необходимо изменить конфигурацию IP-адрес внешнего (Ethernet) обращаться в соответствии с требованиями центра данных конкретного клиента.  
  
> [!NOTE]  
> PDW V1 требуется 8 внешний IP-адрес (*клиентов с выходом*) адреса для предоставления внешнего подключения к каждому элемента управления в стойку узлов. 2012 PDW (V2) улучшенные сетевые соединения, предоставляя все компоненты устройства извне через IP-адресов. Такой подход обеспечивает надежность которой снижает расходы, повышает гибкость и расширяет возможности перемещения данных, загрузка данных и интеграции Hadoop. Число требуемые IP-адреса зависит от количество узлов на устройстве. Чтобы адаптировать этот большего размера блока IP-адресов, клиенту необходимо настроить отдельную подсеть для PDW. В этой подсети будет недостаточно IP адресного пространства (до 250 адреса) для размещения компонентов до 5 стеллажей PDW.  
  
**Сетевая конфигурация** страница позволяет просмотреть внешние параметры сети для узлов на устройстве система Analytics Platform System. Эта страница доступна, только для чтения.  
  
![Сеть устройств DWConfig](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Чтобы обновить конфигурацию сети на устройстве  
Изменить IP-адреса структуры домена и домена рабочей нагрузки, изменив **AplianceInfo.xml** файл и затем запустите программу установки. Эта операция выполняется в автономном режиме. Регионы PDW будет автоматически остановлен во время изменение IP-адреса.  
  
> [!NOTE]  
> Доменные имена предоставляются во время установки и указываются вплоть до 6 буквенно-цифровые символы, начиная с буквы. Частые систему именования создает домен фабрики, начиная с F, начиная с P. домена рабочей нагрузки PDW Этот формат, что служба выполняется на протяжении всего файла справки, но не является обязательным. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Чтобы изменить IP-адреса система платформы аналитики  
  
1.  С помощью **удаленного рабочего стола** приложения, подключения к **HST01** с помощью учетной записи администратора домена рабочей нагрузки.  
  
2.  На узле HST01, откройте его модуль во **c:\pdwinst\media\AplianceInfo.xml**.  
  
    > [!NOTE]  
    > Если файл отсутствует, может потребоваться создать новый файл.  
  
3.  Обновите значения IP-адрес Ethernet, при необходимости и сохраните файл.  
  
4.  В окне командной строки выполните следующую команду установки для обновления IP-адресов для региона PDW, с помощью P/F/H доменные имена и пароли администратора.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Производитель ссылки  
Дополнительные сведения о модулях Dell см. в разделе:  
  
-   Инструкции PowerConnect Switch [Dell PowerConnect 6200 системная CLI ссылаются на руководство по](https://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC [руководство пользователя интегрированной Dell удаленного доступа контроллера 7 (iDRAC7) версии 1.30.30](https://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU **Dell измеряются Rack PDU**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>См. также  
[Запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
