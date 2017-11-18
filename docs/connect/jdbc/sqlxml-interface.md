---
title: "Интерфейс SQLXML | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c636345439175c516b647a2951ac3bfa8824b06
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlxml-interface"></a>Интерфейс SQLXML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который реализует интерфейс java.sql.SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. **SQLXML** сопоставляется с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** тип данных.  
  
 Интерфейс SQLXML обеспечивает методы для доступа к значению XML в виде **строка**, **чтения** или **записи**, или как **поток**. Значения XML можно также получить через **источника** или задается как **результат**, которых используется API-интерфейсами синтаксического анализа XML как объектной модели документа (DOM), простой API-Интерфейс для XML (SAX) и Streaming API for XML (StAX) как также, как с помощью XSLT преобразует и XPath.  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице приводится описание методов, определенных в интерфейсе SQLXML.  
  
|Синтаксис метода|Описание метода|  
|-------------------|------------------------|  
|[void free()](http://go.microsoft.com/fwlink/?LinkId=131685)|Этот метод освобождает объект SQLXML и ресурсы, занятые им.|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|Возвращает входной поток для чтения данных из SQLXML.|  
|[Модуль чтения getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|Возвращает **XML** данных в виде объекта java.io.Reader или потока символов.|  
|[T расширяет getSource T источника (класс\<T > sourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|Возвращает **источника** для чтения **XML** значение, заданное данным **SQLXML** объекта.<br /><br /> **Примечание:** getSource метод поддерживает следующие источники: javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource и java.io.InputStream.|  
|[Строка getString()](http://go.microsoft.com/fwlink/?LinkId=131757)|Возвращает строковое представление **XML** значение, указанное объектом SQLXML.|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|Извлекает поток, который может быть использован для записи **XML** значения, представляемого данным объектом SQLXML.|  
|[Модуль записи setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|Возвращает поток, используемый для записи **XML** значения, представляемого данным объектом SQLXML.|  
|[T расширяет setResult T результат (класс\<T > resultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|Возвращает **результат** для параметра **XML** значение, заданное данным **SQLXML** объекта.<br /><br /> **Примечание:** setResult метод поддерживает следующие источники: javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult и java.io.OutputStream.|  
|[void setString(String value)](http://go.microsoft.com/fwlink/?LinkId=131762)|Задает значение XML, заданное данным объектом SQLXML для указанного **строка** представление.|  
  
 Приложения могут читать XML-значения в объекте SQLXML или записывать их только один раз.  
  
 При вызове метода free() объект SQLXML становится недействительным и не является доступной для чтения или для записи. Если приложение пытается вызвать метод для этого объекта SQLXML, отличный от метода free(), создается исключение.  
  
 Объект SQLXML становится ни для чтения, ни для записи, когда приложение вызывает любой из следующих методов считывания: getSource getCharacterStream, getBinaryStream и getString.  
  
 Объект SQLXML становится ни для записи, ни для чтения, когда приложение вызывает любой из следующих методов задания: setResult, setCharacterStream, setBinaryStream и setString.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка XML-данных](../../connect/jdbc/supporting-xml-data.md)  
  
  

