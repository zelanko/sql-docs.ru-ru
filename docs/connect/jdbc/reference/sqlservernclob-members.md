---
title: Элементы SQLServerNClob | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55bc36ca4d6bcf6337598ddf6ec6ea8bb905dae2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlservernclob-members"></a>Элементы SQLServerNClob
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Бесплатно](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|Этот метод освобождает **NCLOB** объекта и освобождает ресурсы, занятые им.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|Извлекает **NCLOB** обозначенный значение **java.sql.NClob** объектом в ASCII-потоке.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|Извлекает **NCLOB** обозначенный значение **java.sql.NClob** объекта.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|Извлекает копию указанной подстроки в **NCLOB** обозначенный значение **java.sql.NClob** объекта.|  
|[длина](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|Возвращает число символов в **NCLOB** обозначенный значение **java.sql.NClob** объекта.|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|Возвращает позицию символа указанного **java.sql.NClob** объекта или подстроки в **java.sql.NClob** по указанной начальной позиции.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|Получает поток, который используется для записи ASCII символов, которое необходимо **NCLOB** этим **java.sql.NClob** представляет, начиная с указанной позиции.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|Получает поток, используемый для записи поток символов Юникода, **NCLOB** этим **java.sql.NClob** представляет, начиная с указанной позиции.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|Записывает указанный **строка** для **NCLOB** начиная с указанной позиции.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|Усекает **NCLOB** значение до указанной длины.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, наследуемый от|Методы|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>См. также  
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
