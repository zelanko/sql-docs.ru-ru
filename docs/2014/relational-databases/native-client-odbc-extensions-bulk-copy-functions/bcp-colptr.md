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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62689152"
---
# <a name="bcp_colptr"></a>bcp_colptr
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
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *pData*  
 Указатель на копируемые данные. Если привязанный тип данных имеет тип больших значений (например, SQLTEXT или SQLIMAGE), то параметр *pData* может иметь значение null. ЗНАЧЕНИЕ типа *pData* , указывающее, что данные длинных значений будут отправляться в SQL Server фрагментов с помощью [bcp_moretext](bcp-moretext.md).  
  
 Если для *pData* установлено значение null, а столбец, соответствующий привязанному полю, не имеет тип больших значений, **bcp_colptr** завершается ошибкой.  
  
 Дополнительные сведения о типах больших значений см. в разделе [bcp_bind](bcp-bind.md)**.**  
  
 *idxServerCol*  
 Порядковый номер столбца в таблице базы данных, в которую копируются данные. Первый столбец в таблице имеет порядковый номер 1. Порядковый номер столбца возвращается функцией [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Функция **bcp_colptr** позволяет изменить адрес исходных данных для определенного столбца при копировании данных в SQL Server с помощью [bcp_sendrow](bcp-sendrow.md).  
  
 Изначально указатель на пользовательские данные задается вызовом **bcp_bind**. Если адрес данных переменной программы изменяется между вызовами **bcp_sendrow**, можно вызвать **bcp_colptr** , чтобы сбросить указатель на данные. Следующий вызов **bcp_sendrow** отправляет данные, адресованные вызовом **bcp_colptr**.  
  
 Должен существовать отдельный вызов **bcp_colptr** для каждого столбца в таблице, адрес данных которого необходимо изменить.  
  
## <a name="see-also"></a>См. также:  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
