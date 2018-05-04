---
title: Метод CreateObject (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b06643a652cf2642c14dc6125d8972d76658897c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="createobject-method-rds"></a>Метод CreateObject (RDS)
Создает прокси для целевого бизнес-объекта и возвращает указатель на него. Прокси-сервер пакеты и выполняет маршалинг данные заглушки стороне сервера для взаимодействия с бизнес-объект для отправки запросов и данных через Интернет. Для объектов в работе компонента без прокси-серверы используются, и предоставляется только указатель на объект.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Служба удаленных данных поддерживает следующие протоколы: HTTP, HTTPS (по протоколу SSL, HTTP), DCOM и в процессе.  
  
|Протокол|Синтаксис|  
|--------------|------------|  
|HTTP|Объект набора = DataSpace.CreateObject («ProgId», «http://awebsrvr»)|  
|HTTPS|Объект набора = DataSpace.CreateObject («ProgId», «https://awebsrvr»)|  
|DCOM|Объект набора = DataSpace.CreateObject («ProgId», «computername»)|  
|В процессе|Объект набора = DataSpace.CreateObject («ProgId», «»)|  
  
## <a name="parameters"></a>Параметры  
 *Объект*  
 Объектную переменную, результатом которого является объект, это тип, заданный в *ProgID*.  
  
 *Пространство данных*  
 Объектную переменную, которая представляет [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) объект, используемый для создания экземпляра объекта.  
  
 *Идентификатор progID*  
 Объект **строка** значение, содержащее программный идентификатор, указывающий серверные бизнес-объект, реализующий приложения бизнес-правила.  
  
 *awebsrvr* или *computername*  
 Объект **строка** значение, представляющее URL-адрес, идентифицирующий Internet Information Services (IIS) веб-сервере, где создается экземпляр бизнес-объекта сервера.  
  
## <a name="remarks"></a>Замечания  
 *Протокол HTTP* — стандартные веб-протокол; *HTTPS* — безопасное веб-протокол. Используйте *протокол DCOM* при выполнении локальной сети без HTTP. *В процессе* протоколом является локальной библиотеки динамической компоновки (DLL); он не использует сеть.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataSpace (служба удаленных рабочих столов)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Объект DataFactory, метод запроса и пример метода CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [Пространство данных объект и метод CreateObject примере (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [Метод CreateRecordset (служба удаленных рабочих столов)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


