---
description: Метод ConvertToString (служба удаленных рабочих столов)
title: Метод ConvertToString (RDS) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 58bfb25264c15f051bfd7144bdcaf01bbd1eda05
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439196"
---
# <a name="converttostring-method-rds"></a>Метод ConvertToString (служба удаленных рабочих столов)
Преобразует [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) в строку MIME, представляющую данные набора записей.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataFactory*  
 Объектная переменная, представляющая объект [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) DataObject.  
  
 *набор записей*  
 Объектная переменная, представляющая объект **набора записей** .  
  
## <a name="remarks"></a>Remarks  
 С помощью файлов. ASP используйте **ConvertToString** для внедрения **набора записей** в HTML-страницу, созданную на сервере для передачи его на клиентский компьютер.  
  
 **ConvertToString** сначала загружает **набор записей** в таблицы службы курсоров, а затем создает поток в формате MIME.  
  
 На клиенте служба удаленных данных может преобразовать строку MIME обратно в полностью работоспособный **набор записей**. Он хорошо работает для обработки менее чем 400 строк данных, при этом длина строки не превышает 1024 байт. Его не следует использовать для потоковой передачи данных больших двоичных объектов и больших результирующих наборов по протоколу HTTP. В строке не выполняется никакого сжатия, поэтому очень большие наборы данных занимают значительное время для передачи по протоколу HTTP по сравнению с форматом таблеграм, оптимизированным для обработки и развернутым службой Remote Data Service в качестве собственного формата транспортного протокола.  
  
> [!NOTE]
>  Если вы используете Active Server страницы для внедрения полученной строки MIME на клиентской HTML-странице, имейте в виду, что версии VBScript, предшествующие версии 2,0, ограничивают размер строки до 32 000. Если это ограничение превышено, возвращается ошибка. При использовании внедрения MIME с помощью файлов. ASP следует относительно малый масштаб запроса. Чтобы устранить эту проблему, скачайте последнюю версию VBScript с веб-сайта технологий Microsoft Windows Script.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода ConvertToString (Visual Basic)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [Пример метода ConvertToString (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


