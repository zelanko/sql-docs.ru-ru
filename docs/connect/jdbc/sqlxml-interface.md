---
title: Интерфейс SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6257f3575412bc35b00722a0b5da6b8c5ca74f10
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47816002"
---
# <a name="sqlxml-interface"></a>Интерфейс SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который реализует интерфейс java.sql.SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. **SQLXML** сопоставляется с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xml** тип данных.  
  
Интерфейс SQLXML обеспечивает методы для доступа к значению XML в виде **строка**, **чтения** или **записи**, или как **Stream**. Обратиться к значению XML можно также через свойство **Source**, а задать его — через свойство **Result**. Эти свойства используются интерфейсами API синтаксического анализатора XML, такими как модель DOM, простой интерфейс API для XML (SAX) и потоковый интерфейс API для XML (StAX), а также преобразованиями XSLT и XPath.  
  
## <a name="remarks"></a>Remarks  

В следующей таблице приводится описание методов, определенных в интерфейсе SQLXML.  
  
|Синтаксис метода|Описание метода|  
|-------------------|------------------------|  
|[void free()](http://go.microsoft.com/fwlink/?LinkId=131685)|Этот метод освобождает объект SQLXML и ресурсы, занятые им.|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|Возвращает входной поток для чтения данных из SQLXML.|  
|[Reader getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|Возвращает данные **XML** в виде объекта java.io.Reader или потока символов.|  
|[T extends Source T getSource(Class\<T> sourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|Возвращает **источника** для чтения **XML** значение, указанное в этом **SQLXML** объекта.<br /><br /> **Примечание**. Метод getSource поддерживает следующие источники: javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource и java.io.InputStream.|  
|[String getString()](http://go.microsoft.com/fwlink/?LinkId=131757)|Возвращает строковое представление значения **XML**, указанного данным объектом SQLXML.|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|Извлекает поток, который может быть использован для записи значения **XML**, представляемого данным объектом SQLXML.|  
|[Writer setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|Возвращает поток, который должен быть использован для записи значения **XML**, представляемого данным объектом SQLXML.|  
|[T extends Result T setResult(Class\<T> resultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|Возвращает **результат** параметра **XML** значение, указанное в этом **SQLXML** объекта.<br /><br /> **Примечание**. Метод setResult поддерживает следующие источники: javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult и java.io.OutputStream.|  
|[void setString(String value)](http://go.microsoft.com/fwlink/?LinkId=131762)|Задает значение XML, назначенное данным объектом SQLXML для указанного представления **String**.|  
  
Приложения могут читать XML-значения в объекте SQLXML или записывать их только один раз.  
  
При вызове метода free() объект SQLXML становится недействительным: его больше нельзя прочесть или записать в него значения. Если приложение пытается вызвать для этого объекта SQLXML метод, отличный от метода free(), возникает исключение.  
  
Объект SQLXML становится ни читаемым, ни для записи, когда приложение вызывает любой из следующих методов считывания: getSource, getCharacterStream, getBinaryStream и getString.  
  
Объект SQLXML больше нельзя будет доступной для чтения при приложение вызовет какой-либо из следующих методов задания: setResult, setCharacterStream, setBinaryStream и setString.  
  
## <a name="see-also"></a>См. также:  

[Поддержка XML-данных](../../connect/jdbc/supporting-xml-data.md)  
