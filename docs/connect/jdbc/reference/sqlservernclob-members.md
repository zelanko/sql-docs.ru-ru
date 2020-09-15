---
description: Элементы SQLServerNClob
title: Элементы SQLServerNClob | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e23a4a5e9a4cb2d2c2a7ecd93db8615e814652c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354460"
---
# <a name="sqlservernclob-members"></a>Элементы SQLServerNClob
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены элементы класса [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|Этот метод освобождает объект **NCLOB** и ресурсы, занятые им.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|Извлекает значение **NCLOB**, обозначенное объектом **java.sql.NClob** в ASCII-потоке.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|Извлекает значение **NCLOB**, обозначенное объектом **java.sql.NClob**.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|Извлекает копию указанной подстроки из значения **NCLOB**, обозначенного объектом **java.sql.NClob**.|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|Получает число символов в значении **NCLOB**, обозначенном объектом **java.sql.NClob**.|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|Извлекает положение символа указанного объекта **java.sql.NClob** или подстроки в **java.sql.NClob** с учетом указанной начальной позиции.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|Извлекает поток, используемый для записи символов ASCII в значение **NCLOB**, представленное данным объектом **java.sql.NClob**, начиная с указанной позиции.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|Извлекает поток, используемый для записи символов Юникода в значение **NCLOB**, представленное этим объектом **java.sql.NClob**, начиная с указанной позиции.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|Записывает заданную **строку** в **NCLOB**, начиная с указанной позиции.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|Усекает значение **NCLOB** до указанной длины.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, наследуемый от|Методы|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
