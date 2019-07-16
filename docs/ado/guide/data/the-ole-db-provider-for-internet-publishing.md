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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923906"
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Поставщик OLE DB для публикации в Интернете
ADO [записи](../../../ado/reference/ado-api/record-object-ado.md) и [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объектов можно использовать поставщик Microsoft OLE DB для публикаций в Интернете (поставщика Интернет-публикаций) получить доступ и использовать ресурсы, такие как веб-папки или файлы обслуживаемые Microsoft FrontPage. С помощью ADO можно указать источник **записи**, **Stream**, или [записей](../../../ado/reference/ado-api/recordset-object-ado.md) быть URL-адрес. Вы можно отправить, загрузить, переместить, скопировать и удалите ресурсы или напрямую манипулировать свойства ресурса.  
  
 Пример кода, который использует **записей** и **потоки** публикации поставщика Интернета, см. в разделе [публикации ситуации Интернета](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Службу публикации в Интернете устанавливается вместе с Microsoft Windows 2000. Более ранних версиях службу публикации в Интернете, также доступны с помощью Microsoft Office 2000 и Microsoft Internet Explorer 5.0.  
  
 Существует три способа для подключения ADO службу публикации в Интернете:  
  
-   Укажите «URL-адрес =» в строке подключения. Пример:  
  
    ```  
    objConn.Open "URL=https://servername"  
    ```  
  
-   Укажите Msdaipp.dso для *поставщика* ключевое слово строки подключения. Пример:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=https://servername"  
    ```  
  
-   Укажите Msdaipp.dso для [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Пример:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "https://servername"  
    ```  
  
> [!NOTE]
>  Если Msdaipp.dso явно не указан для параметра поставщика, с помощью *поставщика* ключевое слово строки подключения или **поставщика** свойство, нельзя использовать «URL-адрес =» в строке подключения. В противном случае произойдет ошибка. Вместо этого просто укажите URL-адрес, как показано выше.  
  
 Более конкретные сведения о публикации Интернета, см. в разделе [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), или поставщик документацию, поставляемую с исходным приложением с помощью которого поставщик OLE DB для Был установлен публикаций в Интернете: Windows 2000, Office 2000 или Internet Explorer 5.0.
