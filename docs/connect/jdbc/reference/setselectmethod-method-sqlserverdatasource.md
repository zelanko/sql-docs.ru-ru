---
title: Метод setSelectMethod (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e82bdcef16c854d0bcc1f11757b0bb2ed6030145
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972997"
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Метод setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных при помощи данного объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Параметры  
 *selectMethod*  
  
 Значение **String**, содержащее тип курсора по умолчанию.  
  
## <a name="remarks"></a>Remarks  
 Свойство selectMethod содержит тип курсора по умолчанию, который используется для результирующего набора. Это свойство полезно при работе с крупными результирующими наборами, когда не нужно сохранять результирующий набор целиком в памяти клиента. Если установить это свойство в значение cursor, то можно создать серверный курсор, который будет получать данные меньшими фрагментами. Если свойство selectMethod не задано, метод [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) возвращает значение по умолчанию — direct.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
