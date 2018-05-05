---
title: Свойство InternetTimeout (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 401410dee3c7968c1547e3efa70fe61521b29d6a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="internettimeout-property-rds"></a>Свойство InternetTimeout (RDS)
Указывает количество миллисекунд для ожидания запроса.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** представляет количество миллисекунд до запрос времени ожидания.  
  
## <a name="remarks"></a>Замечания  
 Это свойство применяется только для запросов, отправленных с помощью протоколов HTTP или HTTPS.  
  
 Запросы в трехуровневой среде может занять несколько минут для выполнения. Это свойство позволяет указать дополнительное время для долго выполняющихся запросов.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataSpace (служба удаленных рабочих столов)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример свойства InternetTimeout (Visual Basic)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [Пример свойства InternetTimeout (Visual C++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

