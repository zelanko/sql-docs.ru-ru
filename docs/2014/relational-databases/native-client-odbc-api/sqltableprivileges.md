---
title: SQLTablePrivileges | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 102f8dbaf0746d4f0fd263d7c562b6f74611830c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143964"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
  Функция**SQLTablePrivileges** может быть выполнена для статического курсора. При попытке выполнить метод **SQLTablePrivileges** для обновляемого курсора (динамического или управляемого набором ключей) будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя для *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLTablePrivileges] (http://go.microsoft.com/fwlink/?LinkId=59373\)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
