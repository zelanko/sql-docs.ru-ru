---
description: Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll
title: Коннектионвалидшаредмемори dbmslpcn.dll
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a487eb380ea4e7b0fe246efdb9281cbab63a1303
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475995"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Функция определяет, установлена ли и активна SQL Server общая память.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Параметры  
 *сзсервернаме*  
  
-   Тип: **char \** _  
  
-   Имя сервера SQL Server.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип: _ *bool**  
  
 Возвращает значение 0, если недопустимо; Else возвращает ненулевое значение.  
  
  
