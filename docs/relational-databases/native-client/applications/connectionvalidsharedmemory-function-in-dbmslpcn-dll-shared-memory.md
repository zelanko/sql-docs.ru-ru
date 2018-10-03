---
title: Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb8f36b1e9ab57711a2c24c026130e5b9a6fc382
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718122"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>Функция ConnectionValidSharedMemory в общей памяти dbmslpcn.dll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Функция определяет, является ли SQL Server общей памяти установлен и активен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>Параметры  
 *szServerName*  
  
-   Тип: **char\***  
  
-   Имя сервера SQL Server.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип: **BOOL**  
  
 Возвращает 0, если это не является допустимым; в противном случае возвращает ненулевое значение.  
  
  
