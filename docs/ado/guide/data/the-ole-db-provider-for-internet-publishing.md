---
title: Поставщик OLE DB для публикации в Интернете | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80a373196f98a964bc3e522cc9329907a3392b95
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923906"
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Поставщик OLE DB для публикации в Интернете
Объекты [записи](../../../ado/reference/ado-api/record-object-ado.md) и [потока](../../../ado/reference/ado-api/stream-object-ado.md) ADO можно использовать с поставщиком Microsoft OLE DB для публикации в Интернете (поставщик публикации в Интернете) для доступа к ресурсам, таким как веб-папки или файлы, обслуживаемые Microsoft FrontPage, и управления ими. С помощью ADO можно указать источник **записи**, **потока**или [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) в качестве URL-адреса. Затем можно передать, скачать, переместить, скопировать и удалить ресурсы или напрямую управлять свойствами ресурсов.  
  
 Пример кода, в котором используются **записи** и **потоки** с поставщиком публикации в Интернете, см. в статье [сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Поставщик публикации в Интернете устанавливается вместе с Microsoft Windows 2000. Более ранние версии поставщика услуг публикации в Интернете также доступны в Microsoft Office 2000 и Microsoft Internet Explorer 5,0.  
  
 Существует три способа подключения ADO к поставщику публикации в Интернете:  
  
-   В строке подключения укажите "URL =". Пример:  
  
    ```  
    objConn.Open "URL=https://servername"  
    ```  
  
-   Укажите Мсдаипп. DSO для ключевого слова *provider* в строке подключения. Пример:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=https://servername"  
    ```  
  
-   Укажите Мсдаипп. DSO для свойства [provider](../../../ado/reference/ado-api/provider-property-ado.md) объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) . Пример:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "https://servername"  
    ```  
  
> [!NOTE]
>  Если Мсдаипп. DSO явно задан как значение поставщика с помощью ключевого слова строки подключения *поставщика* или свойства **поставщика** , нельзя использовать "URL =" в строке подключения. В противном случае возникнет ошибка. Вместо этого просто укажите URL-адрес, как показано выше.  
  
 Дополнительные сведения о поставщике публикации в Интернете см. в разделе [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)или в документации поставщика, поставляемой с исходным приложением, с которым установлен поставщик OLE DB для публикации в Интернете: Windows 2000, Office 2000 или Internet Explorer 5,0.
