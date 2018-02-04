---
title: "Настройка несколькими подсетями группы доступности AlwaysOn и экземпляров отказоустойчивых кластеров в Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/1/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: df5182d374e41b68fe35333c6e4ab59714d8241d
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>Настройка несколькими подсетями группы доступности AlwaysOn и экземпляров отказоустойчивых кластеров

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Если всегда в группе доступности (AG) или отработки отказа экземпляра кластера (FCI) охватывает более одного узла, каждый сайт обычно имеет свои собственные сети. Часто это означает, что каждый узел имеет свой собственный IP-адресации. Например адреса сайта А начать с 192.168.1. *x* и 192.168.2 адреса сайта Б. *x*, где *x* — это часть IP-адрес, который является уникальным на сервере. Без какой-то маршрутизации на месте на сетевом уровне эти серверы не смогут взаимодействовать друг с другом. Существует два способа для обработки этого сценария: Настройка сети, связывающим два разных подсетях, известный как виртуальной локальной сети, или настройте маршрутизацию между подсетями.

## <a name="vlan-based-solution"></a>Решение на основе виртуальной ЛС
 
**Необходимое**: решение на основе для виртуальной ЛС, участвующих в группы Доступности или экземпляр отказоустойчивого Кластера необходимо на каждом сервере двух сетевых плат (NIC) правильную доступность (двухпортовый сетевой Адаптер будет единую точку сбоя на физическом сервере), чтобы ее можно назначить IP-адреса на его собственного подсети, а также на виртуальной локальной сети. Это дополнение любых других сведений сети, например iSCSI, которое также требует собственную сеть.

Создание адресов IP для группы Доступности или экземпляр отказоустойчивого Кластера выполняется в виртуальной локальной сети. В следующем примере виртуальной локальной сети имеет подсети 192.168.3. *x*, поэтому 192.168.3.104 IP-адрес, созданных для группы Доступности или экземпляр отказоустойчивого Кластера. Никакой дополнительной необходимо настроить, так как один IP-адрес, назначенный для группы Доступности или экземпляр отказоустойчивого Кластера.

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Конфигурация с Pacemaker

В мире Windows отказоустойчивого кластера Windows Server (WSFC) изначально поддерживает несколько подсетей и обрабатывает несколько IP-адресов через зависимость или IP-адреса. В Linux нет никакой зависимости OR, но отсутствует способ достичь правильную несколькими подсетями в собственном коде, Pacemaker, как показано ниже. Это невозможно, просто используя обычный Pacemaker командной строки для изменения ресурса. Необходимо изменить сведения о кластере базового (CIB). CIB — XML-файл с конфигурацией Pacemaker.

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>Обновление CIB

1.  Экспорт CIB.

    **Red Hat Enterprise Linux (RHEL) и Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    Где *filename* имя, необходимо вызвать CIB.

2.  Измените файл, который был создан. Найдите `<resources>` раздела. Вы увидите различные ресурсы, которые были созданы для группы Доступности или экземпляр отказоустойчивого Кластера. Найти связанную с IP-адрес. Добавить `<instance attributes>` статьи с данными для второй IP-адрес выше или ниже существующей, но перед `<operations>`. Он будет выглядеть примерно как следующий синтаксис:

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    где *NameForAttribute* уникальное имя для этого атрибута *Оценка* — номер, назначенный с атрибутом, который должен быть выше основная подсеть, *RuleName*имя правила, *имя* имя выражения, *NodeNameInSubnet2* имя узла в другие подсети *NameForSecondIP* — имя, связанное с второй IP-адрес *IP-адрес* IP-адрес подсети, второй, *NameForSecondIPNetmask* — имя, связанное с маска подсети, и *Маска* является маска подсети, второй.
    
    Ниже приведен пример.
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  Импортируйте измененный CIB и перенастроить Pacemaker.

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    где *filename* имя файла CIB с измененные данные IP-адресов.

### <a name="check-and-verify-failover"></a>Проверьте и проверьте отработку отказа

1.  После успешного применения CIB обновленной конфигурации проверить связь с DNS-имя, связанное с ресурса IP-адреса в Pacemaker. Оно должно отражать IP-адрес, связанный с подсетью, в настоящее время размещается группы Доступности или экземпляр отказоустойчивого Кластера.
2.  Сбой группы Доступности или экземпляр отказоустойчивого Кластера в другой подсети.
3.  После группы Доступности или экземпляр отказоустойчивого Кластера находится в режиме полного, проверить связь с DNS-имя, связанное с IP-адресом. Он должен отражать IP-адрес в подсети, второй.
4.  При необходимости, обратно в исходный подсети ошибкой группы Доступности или экземпляр отказоустойчивого Кластера.
