---
description: События службы удаленных рабочих столов
title: События RDS | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], RDS
- RDS events [ADO]
ms.assetid: e03739e0-8169-46d6-9956-556b644a7645
author: rothja
ms.author: jroth
ms.openlocfilehash: be38e4897e942e30af61937c326cd2efa16a1fd8
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724375"
---
# <a name="rds-events"></a>События службы удаленных рабочих столов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
|Событие|Описание|  
|-|-|  
|[OnError (RDS)](./onerror-event-rds.md)|Вызывается при возникновении ошибки во время операции.|  
|[onReadyStateChange (RDS)](./onreadystatechange-event-rds.md)|Вызывается при каждом изменении значения свойства **ReadyState** .|