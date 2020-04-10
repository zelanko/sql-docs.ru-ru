---
title: Метод setObject (java.lang.String, java.lang.Object) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setObject (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 14b84409-5510-4642-a83b-732d8511c5b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8cc0f284b504cf0ea0a8d757ed626de360ac7ed
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920828"
---
# <a name="setobject-method-javalangstring-javalangobject"></a>Метод setObject (java.lang.String, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает значение указанного параметра с помощью заданного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setObject(java.lang.String sCol,  
                      java.lang.Object o)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *o*  
  
 Значение **Object**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setObject указывается методом setObject в интерфейсе java.sql.CallableStatement.  
  
 Если задано значение NULL, то этот метод преобразует указанный параметр в тип CHAR перед отправкой в базу данных. Если параметр объявлен с типом SQL binary, varbinary или image, то при выполнении инструкции будет вызвано исключение.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 на работу этого метода влияет свойство подключения **sendTimeAsDatetime** ([Настройка свойств подключения](../../../connect/jdbc/setting-the-connection-properties.md)) и [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в статье [Настройка способа отправки значений java.sql.Time на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setObject (SQLServerCallableStatement)](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
