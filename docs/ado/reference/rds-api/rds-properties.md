---
description: Свойства службы удаленных рабочих столов
title: Свойства RDS | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- RDS properties [ADO]
- properties [ADO], RDS
ms.assetid: e4e04cbd-21fc-44a1-9f21-49aa68746934
author: rothja
ms.author: jroth
ms.openlocfilehash: a4f47967fc80ba488c57299fe7f94c13d9f9e949
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981525"
---
# <a name="rds-properties"></a>Свойства службы удаленных рабочих столов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Свойство|Описание|  
|-|-|  
|[Connect (RDS)](./connect-property-rds.md)|Указывает имя базы данных, из которой выполняются операции запроса и обновления.|  
|[Ексекутеоптионс (RDS)](./executeoptions-property-rds.md)|Указывает, включено ли асинхронное выполнение.|  
|[FetchOptions (RDS)](./fetchoptions-property-rds.md)|Указывает тип асинхронной выборки.|  
|[Филтерколумн (RDS)](./filtercolumn-property-rds.md)|Указывает столбец, по которому вычисляется критерий фильтра.|  
|[Филтеркритерион (RDS)](./filtercriterion-property-rds.md)|Указывает оператор вычисления для использования в значении фильтра.|  
|[FilterValue (RDS)](./filtervalue-property-rds.md)|Указывает значение для фильтрации записей.|  
|[Обработчик (RDS)](./handler-property-rds.md)|Указывает имя программы настройки на стороне сервера (*обработчик*), которая расширяет функциональные возможности **RDSServer.** данных и всех параметров, используемых *обработчиком*.|  
|[InternetTimeout (RDS)](./internettimeout-property-rds.md)|Указывает количество миллисекунд ожидания перед истечением времени ожидания запроса.|  
|[ReadyState (RDS)](./readystate-property-rds.md)|Указывает ход выполнения объекта « **элемент управления** данными», когда он извлекает данные в объект **набора записей** .|  
|[Набор записей и Саурцерекордсет (RDS)](./recordset-sourcerecordset-properties-rds.md)|Указывает объект **набора записей** , возвращенный из пользовательского бизнес-объекта.|  
|[Сервер (RDS)](./server-property-rds.md)|Указывает имя службы IIS (IIS) и протокол связи.|  
|[SortColumn (RDS)](./sortcolumn-property-rds.md)|Указывает, по какому столбцу следует отсортировать записи.|  
|[SortDirection (RDS)](./sortdirection-property-rds.md)|Указывает, используется ли порядок сортировки по возрастанию или по убыванию.|  
|[SQL (RDS)](./sql-property.md)|Указывает строку запроса, используемую для получения **набора записей**.|  
|[URL-АДРЕС (RDS)](./url-property-rds.md)|Указывает строку, содержащую относительный или абсолютный URL-адрес.|