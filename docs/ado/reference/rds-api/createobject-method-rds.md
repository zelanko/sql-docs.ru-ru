---
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
ms.openlocfilehash: 2b8cf7f5629158ccd1bdd74e30b7ba9bc5bb6942
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762675"
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
 *Объектами*  
 Объектная переменная, результатом которой является объект, который является типом, заданным в параметре *ProgID*.  
  
 *Пространство данных*  
 Объектная переменная, представляющая [RDS. Объект пространства](../../../ado/reference/rds-api/dataspace-object-rds.md) данных, используемый для создания экземпляра нового объекта.  
  
 *ID*  
 **Строковое** значение, содержащее программный идентификатор, указывающий бизнес-объект на стороне сервера, который реализует бизнес-правила приложения.  
  
 *авебсрвр* или *ComputerName*  
 **Строковое** значение, представляющее URL-адрес, обозначающий сервер службы IIS (IIS), на котором создается экземпляр бизнес-объекта сервера.  
  
## <a name="remarks"></a>Remarks  
 *Протокол HTTP* является стандартным веб-протоколом. *HTTPS* — это защищенный веб-протокол. Используйте *протокол DCOM* при запуске локальной сети без HTTP. *Внутрипроцессный* протокол — это локальная библиотека динамической КОМПОНОВКИ (DLL); Он не использует сеть.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataSpace (служба удаленных рабочих столов)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта факта, метода запроса и метода CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [Пример объекта пространства и метода CreateObject (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [Метод CreateRecordset (служба удаленных рабочих столов)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


