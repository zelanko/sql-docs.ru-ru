---
title: Функции системы Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca71687887444cafc502c15683f3972cf6308e6b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302835"
---
# <a name="system-functions"></a>Системные функции
В следующей таблице перечислены функции системы, включенные в набор функций масштабирования ODBC. Позвонив по **телефону s'LGetInfo** с *информационным типом* SQL_SYSTEM_FUNCTIONS, приложение может определить, какие системные функции поддерживаются драйвером.  
  
 Аргументы, обозначаемые как *exp,* могут быть названием столбца, результатом другой функции масштабирования или буквального, где базовый тип данных может быть представлен как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP.  
  
 Аргументы, обозначаемые как *значение,* могут быть буквальной константой, где базовый тип данных может быть представлен как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP.  
  
 Возвратные значения представлены как типы данных ODBC.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|**БАЗА ДАННЫх ()** (ODBC 1.0)|Возвращает имя базы данных, соответствующее ручке соединения. (Название базы данных также доступно, позвонив по **телефону s'LGetConnectOption** с опцией SQL_CURRENT_QUALIFIER подключения.)|  
|**IFNULL** _(exp_,_значение)_**)** (ODBC 1.0)|Если *exp* является нулевым, *значение* возвращается. Если *exp* не является недействительным, *exp* возвращается. Возможный тип или типы *значений* данных должны быть совместимы с типом *exp*данных.|  
|**ПОЛЬЗОВАТЕЛЬ( )** (ODBC 1.0)|Возвращает имя пользователя в DBMS. (Имя пользователя также доступно через **S'LGetInfo,** указав тип информации: SQL_USER_NAME.) Это может отличаться от имени входа.|
