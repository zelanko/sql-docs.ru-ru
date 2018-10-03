---
title: bcp_colptr | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 269ab3c748557d1d2870195524310f2371b79c52
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131004"
---
# <a name="bcpcolptr"></a>bcp_colptr
  Устанавливает адрес данных переменных программы для текущей копии в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pData*  
 Указатель на копируемые данные. Если тип привязанных данных является типом больших значений (например SQLTEXT или SQLIMAGE), *pData* может иметь значение NULL. Значение NULL *pData* означает данные большого будет отправлено в SQL Server в виде фрагментов с помощью [bcp_moretext](bcp-moretext.md).  
  
 Если *pData* имеет значение NULL и столбец соответствующий привязанному полю не является типом больших значений **bcp_colptr** завершается ошибкой.  
  
 Дополнительные сведения о типах больших значений см. в разделе [bcp_bind](bcp-bind.md)**.**  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 **Bcp_colptr** функция позволяет изменять адрес источника данных для определенного столбца, при копировании данных в SQL Server с [bcp_sendrow](bcp-sendrow.md).  
  
 Изначально указатель на пользовательские данные устанавливается вызовом **bcp_bind**. Если адрес данных переменных программы изменяется между вызовами **bcp_sendrow**, можно вызвать **bcp_colptr** Чтобы сбросить указатель на данные. Следующий вызов **bcp_sendrow** отправляет данные путем вызова **bcp_colptr**.  
  
 Должен быть отдельный **bcp_colptr** вызова для каждого столбца в таблице, адреса данных которого нужно изменить.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
