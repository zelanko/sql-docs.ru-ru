---
title: Пример метода ConvertToString (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 091ecc7284fb02a8da1bc79e755c6704015736db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780282"
---
# <a name="converttostring-method-rds"></a>Метод ConvertToString (служба удаленных рабочих столов)
Преобразует [записей](../../../ado/reference/ado-api/recordset-object-ado.md) в строку MIME, представляющий данные набора записей.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Фабрики данных*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта.  
  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
## <a name="remarks"></a>Примечания  
 С помощью ASP-файлах, использовать **ConvertToString** для внедрения **записей** на странице HTML, созданный на сервере для его передачи на клиентский компьютер.  
  
 **ConvertToString** сначала загружает **записей** курсора службой таблиц, а затем создает поток в формате MIME.  
  
 На стороне клиента, служба Remote Data Service можно преобразовать строку MIME в полностью функциональный **записей**. Он подходит для обработки менее 400 строк данных с использованием не более 1024 байта ширины каждой строки. Его не следует использовать для потоковой передачи данных больших двоичных ОБЪЕКТОВ и большие результирующие наборы по протоколу HTTP. Без сжатия передачи выполняется в строке, очень больших наборов данных займет значительное время для транспорта по протоколу HTTP, по сравнению с оптимизированной передачи tablegram формат определяются и развертываются с удаленной службы данных, как его формат собственного транспортного протокола.  
  
> [!NOTE]
>  Если вы используете Active Server Pages для внедрения результирующая строка MIME в HTML-страницы клиента, имейте в виду, что версиях VBScript до версии 2.0 ограничивает размер объемом 32 КБ. Если этот предел превышен, возвращается ошибка. Область запроса останется относительно небольшой, при использовании MIME внедрение с помощью ASP-файлах. Чтобы устранить эту проблему, скачайте последнюю версию VBScript из технологий скрипт Windows веб-узел.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода ConvertToString (Visual Basic)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [Пример метода ConvertToString (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


