---
title: SQL Server результаты сообщения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff604f4c5d66a5742868e25ba05ca6b4528ddb1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206711"
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
  Следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции не создают [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные наборы строк поставщика OLE DB клиента или число затронутых строк при выполнении:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB возвращает S_OK, и сообщения становятся доступными потребителю поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает S_OK и имеет одно или несколько информационных сообщений, доступных после выполнения множества [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций или выполнения пользовательской функции- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] члена поставщика собственного клиента OLE DB.  
  
 Потребитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB собственного клиента, который разрешает динамической спецификации текста запроса, должен проверять интерфейсы ошибок после каждого выполнения функции-члена независимо от значения кода возврата, наличия или отсутствия возвращенной ссылки на интерфейс **IRowset** или **IMultipleResults** или количества затронутых строк.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](errors.md)  
  
  
