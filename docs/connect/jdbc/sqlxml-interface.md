---
title: Интерфейс SQLXML | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72cccce89d5e30a92f38b956c8b7996949d3bb46
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027692"
---
# <a name="sqlxml-interface"></a>Интерфейс SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер JDBC обеспечивает поддержку API JDBC 4.0, который реализует интерфейс java.sql.SQLXML. Интерфейс SQLXML определяет методы для обмена данными XML и их обработки. Тип данных **SQLXML** сопоставляется с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**xml**.  
  
Интерфейс SQLXML предоставляет методы для доступа к значению XML в формате **String**, **Reader** или **Writer**, а также **Stream**. Обратиться к значению XML можно также через свойство **Source**, а задать его — через свойство **Result**. Эти свойства используются интерфейсами API синтаксического анализатора XML, такими как модель DOM, простой интерфейс API для XML (SAX) и потоковый интерфейс API для XML (StAX), а также преобразованиями XSLT и XPath.  
  
## <a name="remarks"></a>Remarks  

В следующей таблице приводится описание методов, определенных в интерфейсе SQLXML.  
  
|Синтаксис метода|Описание метода|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|Этот метод освобождает объект SQLXML и ресурсы, занятые им.|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|Возвращает входной поток для чтения данных из SQLXML.|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|Возвращает данные **XML** в виде объекта java.io.Reader или потока символов.|  
|[T extends Source T getSource(Class\<T> sourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|Возвращает объект **Source** (источник) для чтения значения **XML**, заданного этим объектом **SQLXML**.<br /><br /> **Примечание.**  Метод getSource поддерживает следующие источники: javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource и java.io.InputStream.|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|Возвращает строковое представление значения **XML**, указанного данным объектом SQLXML.|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|Извлекает поток, который может быть использован для записи значения **XML**, представляемого данным объектом SQLXML.|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|Возвращает поток, который должен быть использован для записи значения **XML**, представляемого данным объектом SQLXML.|  
|[T extends Result T setResult(Class\<T> resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|Возвращает объект **Result** (результат) для записи значения **XML**, заданного этим объектом **SQLXML**.<br /><br /> **Примечание.** Метод setResult поддерживает следующие источники: javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult и java.io.OutputStream.|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|Задает значение XML, назначенное данным объектом SQLXML для указанного представления **String**.|  
  
Приложения могут читать XML-значения в объекте SQLXML или записывать их только один раз.  
  
При вызове метода free() объект SQLXML становится недействительным: его больше нельзя прочесть или записать в него значения. Если приложение пытается вызвать для этого объекта SQLXML метод, отличный от метода free(), возникает исключение.  
  
Объект SQLXML больше нельзя будет прочесть или записать в него значения, если приложение вызовет любой из следующих методов считывания: getSource, getCharacterStream, getBinaryStream или getString.  
  
Объект SQLXML больше нельзя будет прочесть или записать в него значения, если приложение вызовет любой из следующих методов записи: setResult, setCharacterStream, setBinaryStream или setString.  
  
## <a name="see-also"></a>См. также раздел  

[Поддержка данных XML](../../connect/jdbc/supporting-xml-data.md)  
