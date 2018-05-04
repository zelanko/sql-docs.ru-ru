---
title: Драйвер ODBC для Oracle | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 950caf4fe5d5160def82c5b668541780980d706d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-driver-for-oracle"></a>Драйвер ODBC для Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC Microsoft® для Oracle позволяет подключить приложение ODBC-совместимую с базой данных Oracle. Драйвер ODBC для Oracle соответствует спецификации Open Database Connectivity (ODBC), описанные в *справочнике программиста ODBC*. Он обеспечивает доступ к пакетов PL/SQL, XA и DTC интеграции и Oracle доступ в Internet Information Services (IIS).  
  
 Реляционной СУБД Oracle является системой управления многопользовательской реляционной базы данных, работающей с различными операционными системами рабочей станции и миникомпьютер. IBM-совместимых компьютерах под управлением Microsoft Windows могут взаимодействовать с серверами баз данных Oracle по сети. Поддерживаемые сети состоят из Microsoft LAN Manager, NetWare, VINES, DECnet и какой-либо сети, поддерживающий протокол TCP/IP.  
  
 Драйвер ODBC для Oracle позволяет приложению получить доступ к данным в базе данных Oracle через интерфейс ODBC. Драйвер можно получить доступ к локальным базам данных Oracle или может обмениваться данными с сетью через SQL * Net. В приведенной ниже схеме показана архитектура этот драйвер и приложение.  
  
 ![Драйвер ODBC для Oracle приложения&#47;архитектура драйвера](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Драйвер ODBC для Oracle следует API соответствия уровня 1 и базового уровня совместимости SQL. Оно также поддерживает некоторые функции в API соответствия уровня 2 и большинство грамматики в основные и расширенные SQL уровни соответствия. Драйвер ODBC 2.5 совместимые и поддерживает 32-разрядных системах. Oracle 7.3 x поддерживается полностью; Oracle8 имеется ограниченная поддержка. Драйвер ODBC для Oracle не поддерживает новые типы данных Oracle8 — данные в Юникоде, BLOB, CLOB, и так далее — и не поддерживает Oracle в новой реляционной модели объектов. Дополнительные сведения о поддерживаемых типах данных см. в разделе [поддерживаемые типы данных](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) в данном руководстве.  
  
 Для доступа к данным Oracle, необходимы следующие компоненты:  
  
-   Драйвер ODBC для Oracle  
  
-   База данных реляционной СУБД Oracle  
  
-   Клиентское программное обеспечение Oracle  
  
 Кроме того для удаленных подключений:  
  
-   Сеть, которая подключается к компьютерам под управлением драйвер и базы данных. Сеть должен поддерживать SQL * Net подключений.  
  
## <a name="component-documentation"></a>Компонент документации  
 Это руководство содержит подробные сведения об установке и настройке драйвер Microsoft ODBC для Oracle и добавление программный функциональных возможностей. Он также содержит технические справочные материалы.  
  
 Сведения о конкретных поведение продукта Oracle см. в документации продукта Oracle.  
  
 Сведения об установке или настройке драйвер Microsoft ODBC для Oracle, с помощью администратора источников данных ODBC см. в разделе [администратор источников данных ODBC](../../odbc/admin/odbc-data-source-administrator.md) документации.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Руководство пользователя драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Справочник по программирования драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
