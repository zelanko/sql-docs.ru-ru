---
title: bcp_collen | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a66a88a61a581dff262fb8585b5cf32830f8eeed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137974"
---
# <a name="bcpcollen"></a>bcp_collen
  Устанавливает длину данных в переменной программы для текущего массового копирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *cbData*  
 Длина данных в переменной программы, не включая длину признака длины или конца данных. Установка параметра *cbData* в значение SQL_NULL_DATA означает все строки, скопированные на сервер, которые содержат в столбце значение NULL. Установка в значение SQL_VARLEN_DATA означает, что для определения длины скопированных данных используется признак конца строки или другой метод. Если существует как признак длины, так и признак конца, система использует результат с меньшим количеством скопированных данных.  
  
 *idxServerCol*  
 Порядковый номер столбца таблицы, в которую копируются данные. Первый столбец имеет номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Функция **bcp_collen** позволяет изменять для определенного столбца длину данных в переменной программы при копировании данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции [bcp_sendrow](bcp-sendrow.md).  
  
 Первоначальная длина данных определяется при вызове функции [bcp_bind](bcp-bind.md) . Если длина данных изменяется между вызовами функции **bcp_sendrow** и не используется ни одного префикса длины или признака конца, то для сброса длины можно вызвать **bcp_collen** . При следующем вызове функции **bcp_sendrow** используется длина, заданная функцией **bcp_collen**.  
  
 Для каждого столбца таблицы, длину данных которого нужно изменить, необходимо вызвать функцию **bcp_collen** .  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
