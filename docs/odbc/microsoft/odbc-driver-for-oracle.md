---
title: Драйвер ODBC для Oracle (ru) Документы Майкрософт
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
ms.openlocfilehash: 2b5f1aabd23a587e681c33aed4b4119523444219
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80402614"
---
# <a name="odbc-driver-for-oracle"></a>Драйвер ODBC для Oracle
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте [драйвер ODBC, предоставленный Oracle.](https://www.oracle.com/database/technologies/releasenote-odbc-ic.html)  
  
 Драйвер ODBC корпорации Майкрософт® для Oracle позволяет подключить приложение, соответствующее ODBC, к базе данных Oracle. Драйвер ODBC для Oracle соответствует спецификации Open Database Connectivity (ODBC), описанной в *справочнике программиста ODBC.* Он позволяет получить доступ к пакетам PL/S'L, интеграции XA/DTC и Oracle в рамках информационных служб Интернета (IIS).  
  
 Oracle RDBMS — это многопользовательская система управления реляционными базами данных, работающая с различными рабочими станциями и миникомпьютерными операционными системами. Совместимые с IBM компьютеры под управлением Microsoft Windows могут общаться с серверами баз данных Oracle по сети. Поддерживаемые сети включают Microsoft LAN Manager, NetWare, VINES, DECnet и любую сеть, поддерживающую TCP/IP.  
  
 Драйвер ODBC для Oracle позволяет приложению получать доступ к данным в базе данных Oracle через интерфейс ODBC. Водитель может получить доступ к локальным базам данных Oracle или общаться с сетью через S'L-Net. Следующая диаграмма детализирует это приложение и архитектуру драйвера.  
  
 ![Драйвер ODBC для oracle приложение&#47;архитектурой драйверов](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Драйвер ODBC для Oracle соответствует уровню соответствия API 1 и ядре уровня соответствия S'L. Он также поддерживает некоторые функции в API Соответствие Уровень 2 и большинство грамматики в основных и расширенных уровнях соответствия S'L. Водитель совместим с ODBC 2.5 и поддерживает 32-битные системы. Oracle 7.3x поддерживается полностью; Oracle8 имеет ограниченную поддержку. OdBC Driver для Oracle не поддерживает ни один из новых типов данных Oracle8 - типы данных Unicode, BLOBs, CLOBs и так далее - и не поддерживает новую модель реляционных объектов Oracle. Для получения дополнительной информации о поддерживаемых типах данных [см.](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
 Для доступа к данным Oracle требуются следующие компоненты:  
  
-   Драйвер ODBC для Oracle  
  
-   База данных Oracle RDBMS  
  
-   Программное обеспечение для клиентов Oracle  
  
 Кроме того, для удаленных соединений:  
  
-   Сеть, которая соединяет компьютеры, которые управляют драйвером и базой данных. Сеть должна поддерживать соединения S'L-Net.  
  
## <a name="component-documentation"></a>Документация компонентов  
 Это руководство содержит подробную информацию о настройке и настройке драйвера Microsoft ODBC для Oracle и добавлении программной функциональности. Он также содержит технический справочный материал.  
  
 Для получения информации о конкретном поведении продукта Oracle проконсультируйтесь с документацией, которая сопровождает продукт Oracle.  
  
 Для получения информации о настройке или настройке драйвера Microsoft ODBC для [ODBC Data Source Administrator](../../odbc/admin/odbc-data-source-administrator.md) Oracle с помощью администратора ODBC Data Source см.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Руководство пользователя драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Справочник по программирования драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
