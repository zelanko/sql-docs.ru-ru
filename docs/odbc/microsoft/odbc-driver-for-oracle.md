---
description: Драйвер ODBC для Oracle
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a561539ff960dfa6691d26496b1b62d2ee8ae763
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449336"
---
# <a name="odbc-driver-for-oracle"></a>Драйвер ODBC для Oracle
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Драйвер Microsoft® ODBC для Oracle позволяет подключать приложение, совместимое с ODBC, к базе данных Oracle. Драйвер ODBC для Oracle соответствует спецификации ODBC, описанной в *справочнике программиста по ODBC*. Он обеспечивает доступ к пакетам PL/SQL, интеграции XA/DTC и Oracle Access из службы IIS (IIS).  
  
 Oracle РСУБД — это многопользовательская система управления реляционными базами данных, которая работает с различными операционными системами рабочей станции и миникомпутер. IBM-совместимые компьютеры под управлением Microsoft Windows могут взаимодействовать с серверами базы данных Oracle по сети. Поддерживаются следующие сети: Microsoft LAN Manager, NetWare, VINEs, DECNet и любая сеть, поддерживающая TCP/IP.  
  
 Драйвер ODBC для Oracle позволяет приложению получать доступ к данным в базе данных Oracle через интерфейс ODBC. Драйвер может обращаться к локальным базам данных Oracle или может взаимодействовать с сетью через SQL * NET. На схеме ниже представлены сведения об архитектуре приложения и драйвера.  
  
 ![Архитектура драйвера ODBC для приложения Oracle&#47;](../../odbc/microsoft/media/orcdrvsdkarch.gif "оркдрвсдкарч")  
  
 Драйвер ODBC для Oracle соответствует уровню соответствия API уровня 1 и уровню соответствия SQL. Он также поддерживает некоторые функции в уровне соответствия API 2 и большую часть грамматики в ядре и расширенном уровне соответствия SQL. Драйвер совместим с ODBC 2,5 и поддерживает 32-разрядные системы. Oracle 7.3 x поддерживается полностью; Oracle8 имеет ограниченную поддержку. Драйвер ODBC для Oracle не поддерживает новые типы данных Oracle8 — типы данных в Юникоде, большие двоичные объекты, CLOB и т. д. не поддерживает новую модель реляционных объектов Oracle. Дополнительные сведения о поддерживаемых типах данных см. в разделе [Поддерживаемые типы данных](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) этого руководством.  
  
 Для доступа к данным Oracle требуются следующие компоненты:  
  
-   Драйвер ODBC для Oracle  
  
-   База данных Oracle RDBMS  
  
-   Клиентское по Oracle  
  
 Кроме того, для удаленных подключений:  
  
-   Сеть, соединяющая компьютеры, на которых выполняется драйвер и база данных. Сеть должна поддерживать подключения SQL * NET.  
  
## <a name="component-documentation"></a>Документация по компонентам  
 Это краткое описание содержит подробные сведения о настройке и настройке драйвера Microsoft ODBC для Oracle, а также о добавлении программных функций. Он также содержит технические справочные материалы.  
  
 Сведения о конкретном поведении продукта Oracle см. в документации, прилагаемой к продукту Oracle.  
  
 Сведения о настройке и настройке драйвера Microsoft ODBC для Oracle с помощью администратора источников данных ODBC см. в документации [администратора источников данных ODBC](../../odbc/admin/odbc-data-source-administrator.md) .  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Руководство пользователя драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Справочник по программирования драйвера ODBC для Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
