---
title: Конфигурация сети устройства
description: Устройство аналитики платформы (ТД) создается и настраивается с набором IP-адресов на всех серверах и применимых устройствах из цеха фабрики оборудования. После доставки устройства необходимо перенастроить внешний IP-адрес (Ethernet), чтобы он соответствовал требованиям конкретного клиента к центру обработки данных.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: af892cbb43b42953732bda59d371e3e22855413b
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401409"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Сетевая конфигурация устройства для системы аналитики
Устройство аналитики платформы (ТД) создается и настраивается с набором IP-адресов на всех серверах и применимых устройствах из цеха фабрики оборудования. После доставки устройства необходимо перенастроить внешний IP-адрес (Ethernet), чтобы он соответствовал требованиям конкретного клиента к центру обработки данных.  
  
> [!NOTE]  
> PDW V1 требует 8 внешних*IP-адресов*, чтобы обеспечить внешнее подключение к каждому узлу стойки управления. PDW 2012 (v2) расширенные сетевые подключения, предоставляя каждому компоненту устройства внешний доступ через IP-адреса. Такой подход обеспечивает более надежную структуру, что сокращает затраты и повышает гибкость и улучшает перемещение данных, загрузку данных и интеграцию с Hadoop. Количество требуемых IP-адресов зависит от количества узлов в устройстве. Чтобы разместить этот большой блок IP-адресов, клиент должен настроить отдельную подсеть для PDW. В этой подсети будет достаточно пространства IP-адресов (до 250 адресов) для размещения компонентов до 5 стоек PDW.  
  
Страница **Конфигурация сети** позволяет просматривать сетевые параметры сети для узлов на устройстве системы аналитики. Эта страница доступна только для чтения.  
  
![Сеть устройств DWConfig](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Обновление конфигурации сети на устройстве  
Измените IP-адреса домена структуры и домена рабочей нагрузки, изменив файл **аплианцеинфо. XML** , а затем запустив программу установки. Эта операция выполняется в автономном режиме. При изменении IP-адреса регионы PDW будут автоматически остановлены.  
  
> [!NOTE]  
> Доменные имена предоставляются во время установки и задаются длиной до 6 буквенно-цифровых символов, начиная с буквы. Часто система именования создает домен структуры, начинающийся с F, домен рабочей нагрузки PDW, начиная с P. Этот формат предполагается в разделах файлов справки, но не является обязательным. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Изменение IP-адресов в системе платформы аналитики  
  
1.  С помощью приложения **Удаленный рабочий стол** подключитесь к **HST01** с помощью учетной записи администратора домена рабочей нагрузки.  
  
2.  На узле HST01 откройте файл сведений об устройстве по адресу **к:\пдвинст\медиа\аплианцеинфо.ксмл**.  
  
    > [!NOTE]  
    > Если файл отсутствует, может потребоваться создать новый файл.  
  
3.  При необходимости обновите значения IP-адреса Ethernet и сохраните файл.  
  
4.  В окне командной строки выполните следующую команду установки, чтобы обновить IP-адреса для региона PDW, используя имена доменов P/F/H и пароли администратора.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Справочники производителя  
Дополнительные сведения об устройствах Dell см. в следующих статьях:  
  
-   Инструкции коммутатора PowerConnect руководство по использованию [CLI системы Dell PowerConnect серии 6200](https://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   [встроенное в Идрак/BMC интегрированного контроллера Dell Remote Access Controller 7 (iDRAC7) версии 1.30.30](https://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   **PDU в стоечном исполнении Dell с отслеживанием** энергопотребления`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>См. также  
[Запустите систему Configuration Manager &#40;Analytics Platform&#41;](launch-the-configuration-manager.md)  
  
