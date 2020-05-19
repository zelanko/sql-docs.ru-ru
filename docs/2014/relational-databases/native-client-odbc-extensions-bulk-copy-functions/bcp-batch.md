---
title: bcp_batch | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a37bafc9bac2601e3914455f431c639bce385f48
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705352"
---
# <a name="bcp_batch"></a>bcp_batch
  Фиксирует все строки, которые ранее были скопированы из переменных программы с использованием массовой операции и переданы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью функции [bcp_sendrow](bcp-sendrow.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
## <a name="returns"></a>Возвращаемое значение  
 Количество строк, сохраненных после последнего вызова **bcp_batch**, или -1 в случае ошибки.  
  
## <a name="remarks"></a>Remarks  
 Пакеты массового копирования определяют транзакции. Если приложение использует функции [bcp_bind](bcp-bind.md) и **bcp_sendrow** для массового копирования строк из переменных программы в таблицы SQL Server, то строки фиксируются только при вызове программой функций **bcp_batch** или [bcp_done](bcp-done.md).  
  
 Функцию **bcp_batch** можно вызывать один раз для каждых *n* строк или при приостановке поступления данных (например, в телеметрических приложениях). Если приложение не вызывает функцию **bcp_batch** , то строки, для которых выполнено массовое копирование, фиксируются только при вызове функции **bcp_done** .  
  
## <a name="see-also"></a>См. также  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
