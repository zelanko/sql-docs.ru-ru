---
description: Метод CreateObject (служба удаленных рабочих столов)
title: Метод CreateObject (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fbc77fd5107e5642ba4fabe2f331c803ffde392
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768643"
---
# <a name="createobject-method-rds"></a>Метод CreateObject (служба удаленных рабочих столов)
Создает прокси-сервер для целевого бизнес-объекта и возвращает указатель на него. Прокси-пакеты и маршалирует данные в заглушку на стороне сервера для взаимодействия с бизнес-объектом для отправки запросов и данных через Интернет. Для объектов внутрипроцессного компонента прокси-серверы не используются, предоставляется только указатель на объект.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Служба Remote Data Service поддерживает следующие протоколы: HTTP, HTTPS (HTTP через уровень защищенных сокетов), DCOM и внутрипроцессный.  
  
|Протокол|Синтаксис|  
|--------------|------------|  
|HTTP|Set Object = DataObject. CreateObject ("ProgId", "HTTPS \: //авебсрвр")|  
|HTTPS|Set Object = DataObject. CreateObject ("ProgId", "HTTPS \: //авебсрвр")|  
|DCOM|Set Object = DataObject. CreateObject ("ProgId", "ComputerName")|  
|Внутрипроцессно|Set Object = DataObject. CreateObject ("ProgId", "")|  
  
## <a name="parameters"></a>Параметры  
 *Объект*  
 Объектная переменная, результатом которой является объект, который является типом, заданным в параметре *ProgID*.  
  
 *Пространство данных*  
 Объектная переменная, представляющая [RDS. Объект пространства](./dataspace-object-rds.md) данных, используемый для создания экземпляра нового объекта.  
  
 *ProgID:*  
 **Строковое** значение, содержащее программный идентификатор, указывающий бизнес-объект на стороне сервера, который реализует бизнес-правила приложения.  
  
 *авебсрвр* или *ComputerName*  
 **Строковое** значение, представляющее URL-адрес, обозначающий сервер службы IIS (IIS), на котором создается экземпляр бизнес-объекта сервера.  
  
## <a name="remarks"></a>Remarks  
 *Протокол HTTP* является стандартным веб-протоколом. *HTTPS* — это защищенный веб-протокол. Используйте *протокол DCOM* при запуске локальной сети без HTTP. *Внутрипроцессный* протокол — это локальная библиотека динамической КОМПОНОВКИ (DLL); Он не использует сеть.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataSpace (служба удаленных рабочих столов)](./dataspace-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта факта, метода запроса и метода CreateObject (VBScript)](./datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [Пример объекта пространства и метода CreateObject (VBScript)](./dataspace-object-and-createobject-method-example-vbscript.md)   
 [Метод CreateRecordset (служба удаленных рабочих столов)](./createrecordset-method-rds.md)