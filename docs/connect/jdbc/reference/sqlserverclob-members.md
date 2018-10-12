---
title: Элементы SQLServerClob | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: Assembly
ms.assetid: 7db785ca-edd5-4833-8053-17fdbf87279a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b77219ffbd397b830e1706a84ce5b7ae00aaa6e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736722"
---
# <a name="sqlserverclob-members"></a>Элементы SQLServerClob
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые классом [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md).  
  
## <a name="constructors"></a>Конструкторы  
  
|Имя|Описание|  
|----------|-----------------|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md)|Инициализирует новый экземпляр класса SQLServerClob.|  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlserverclob.md)|Этот метод освобождает объект CLOB и освобождает занятые им ресурсы.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverclob.md)|Материализует Clob в виде потока ASCII.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)|Возвращает данные Clob в виде объекта java.io.Reader или потока символов.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlserverclob.md)|Возвращает копию указанной подстроки в Clob по указанной начальной позиции и числу символов для копирования.|  
|[length](../../../connect/jdbc/reference/length-method-sqlserverclob.md)|Возвращает число символов в Clob.|  
|[position](../../../connect/jdbc/reference/position-method-sqlserverclob.md)|Возвращает позицию символа указанного объекта Clob или подстроки в Clob по указанной начальной позиции.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverclob.md)|Возвращает поток для записи символов ASCII в Clob, начиная с указанной позиции.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverclob.md)|Возвращает поток для записи символов Юникода в Clob, начиная с указанной позиции.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)|Записывает заданную строку в Clob, начиная с указанной позиции.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlserverclob.md)|Усекает Clob до указанной длины.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, наследуемый от|Методы|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
