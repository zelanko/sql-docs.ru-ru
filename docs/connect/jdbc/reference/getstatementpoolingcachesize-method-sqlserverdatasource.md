---
title: Метод getStatementPoolingCacheSize (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ef133c2c661cd9c4778d6ca9b3efec8e51d5a5d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926231"
---
# <a name="getstatementpoolingcachesize-method-sqlserverdatasource"></a>Метод getStatementPoolingCacheSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение свойства подключения **statementPoolingCacheSize**. Возвращает размер кэша подготовленных инструкций для этого подключения. Значение "0" означает, что кэширование не включено.
  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getStatementPoolingCacheSize();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int** для свойства подключения **statementPoolingCacheSize**.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
