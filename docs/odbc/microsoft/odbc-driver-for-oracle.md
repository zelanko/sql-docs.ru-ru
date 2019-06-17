---
title: Драйвер ODBC для Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4685d209d768bd3ff41c1c7367ef6cb6dcd45bcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63043868"
---
# <a name="odbc-driver-for-oracle"></a>Драйвер ODBC для Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC Microsoft® для Oracle позволяет подключить приложение ODBC-совместимую базу данных Oracle. Драйвер ODBC для Oracle соответствует спецификации Open Database Connectivity (ODBC), описанные в *Справочник по программированию ODBC*. Он предоставляет доступ к пакетов PL/SQL, интеграции XA/DTC и Oracle доступ из в Internet Information Services (IIS).  
  
 Реляционной СУБД Oracle — это система управления многопользовательской реляционной базы данных, который выполняется с помощью различных операционных систем рабочих станций и миникомпьютер. IBM-совместимых компьютерах под управлением Microsoft Windows могут взаимодействовать с серверами баз данных Oracle по сети. Поддерживаемые сети включают Microsoft LAN Manager, NetWare, VINES, DECnet и какой-либо сети, которая поддерживает протокол TCP/IP.  
  
 Драйвер ODBC для Oracle позволяет приложению получить доступ к данным в базе данных Oracle через интерфейс ODBC. Драйвер можно получить доступ к локальным базам данных Oracle или он мог обмениваться данными в сети с помощью SQL * Net. В приведенной ниже схеме показана эта архитектура приложений и драйверов.  
  
 ![Драйвер ODBC для Oracle приложения&#47;архитектура драйвера](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Драйвер ODBC для Oracle соответствует 1 уровень соответствия API и базового уровня соответствия SQL. Она также поддерживает некоторые функции в API совместимости уровня 2 и основная часть грамматики в уровни соответствия Core и расширенную SQL. Драйвер ODBC 2,5 требованиям и поддерживает 32-разрядных системах. Oracle 7.3 x поддерживается полностью; Oracle8 обеспечивает ограниченную поддержку. Драйвер ODBC для Oracle не поддерживает новые типы данных Oracle8 - Юникода типов данных, большие двоичные объекты, CLOB и т. д. — и не поддерживает Oracle в новой реляционной модели объектов. Дополнительные сведения о поддерживаемых типах данных см. в разделе [поддерживаемые типы данных](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) в данном руководстве.  
  
 Для доступа к данным Oracle, необходимы следующие компоненты:  
  
-   Драйвер ODBC для Oracle  
  
-   Базу данных реляционной СУБД Oracle  
  
-   Клиентское программное обеспечение Oracle  
  
 Кроме того для удаленных подключений:  
  
-   Сеть, которая подключает компьютеры под управлением драйвер и базе данных. Сети должен поддерживать SQL * Net подключений.  
  
## <a name="component-documentation"></a>Компонент документации  
 Это руководство содержит подробные сведения об установке и настройке драйвер Microsoft ODBC для Oracle и добавление программный функциональных возможностей. Он также содержит технические справочные материалы.  
  
 Сведения о конкретных поведение продуктов Oracle в документации к продукту Oracle.  
  
 Сведения о настройке драйвер Microsoft ODBC для Oracle, с помощью администратора источника данных ODBC, см. в разделе [администратор источников данных ODBC](../../odbc/admin/odbc-data-source-administrator.md) документации.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Руководство пользователя драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Справочник по программирования драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
