---
title: "sys.bandwidth_usage (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bandwidth_usage
- sys.bandwidth_usage
- bandwidth_usage_TSQL
- sys.bandwidth_usage_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.bandwidth_usage
- bandwidth_usage
ms.assetid: 43ed8435-f059-4907-b5c0-193a258b394a
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d30cab1768b293c7cbc2e53729f8e8e8564a53d3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysbandwidthusage-azure-sql-database"></a>sys.bandwidth_usage (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Примечание: Это относится только к [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.**  
  
 Возвращает сведения о пропускной способности сети, используемой каждой базой данных в  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] логический сервер V11**,. Каждая строка, возвращенная для конкретной базы данных, содержит одно направление и класс использования в течение одного часа.  
  
 **Это рекомендуется к использованию в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] логический сервер версии 12.**  
  
 **Sys.bandwidth_usage** представление содержит следующие столбцы.  
  
|Column Name|Description|  
|-----------------|-----------------|  
|**time**|Время (час) использования пропускной полосы. Строки в этом представлении указаны для каждого часа. Например, 2009-09-19 02:00:00.000 означает, что пропускная способность использовалась 19 сентября 2009 г. c 02:00 до 03:00.|  
|**database_name**|Имя базы данных, использовавшей полосу пропускания.|  
|**Направление**|Тип полосы пропускания, которая была использована. Одно из следующих значений.<br /><br /> Входящие: Данные, которые перемещаются в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Исходящий трафик: Данные, которые перемещаются из [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**класс**|Класс полосы пропускания, которая была использована. Одно из следующих значений.<br />Внутренние: Данные, которые перемещаются внутри платформы Azure.<br />Внешние: Данные, которые перемещаются из платформы Azure.<br /><br /> Этот класс возвращается только в том случае, если база данных участвует в связи непрерывного копирования между регионами ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]). If a given database does not participate in any continuous copy relationship, then “Interlink” rows are not returned. Дополнительные сведения см. в подразделе "Замечания" далее в этой статье.|  
|**time_period**|Период времени, происходило потребление — пиковой или непиковое время. The Peak time is based on the region in which the server was created. Например, если сервер был создан в регионе «US_Northwest», параметр Peak определяется как время от 10:00 до 18:00. по тихоокеанскому времени.|  
|**количество**|Объем использованной полосы пропускания в килобайтах (КБ).|  
  
## <a name="permissions"></a>Permissions  
 Это представление доступно только в **master** базы данных для имени входа субъекта серверного уровня.  
  
## <a name="remarks"></a>Замечания  
  
### <a name="external-and-internal-classes"></a>Внешние и внутренние классы  
 Для каждой базы данных, используемые в момент времени **sys.bandwidth_usage** представление возвращает строки, отображающие класс и направление использования пропускной способности. В следующем примере показаны данные, которые могут быть предоставлены для базы данных. В этом примере время 17:00:00 21.04.2012 — это пиковый период. Имя базы данных — Db1. В этом примере **sys.bandwidth_usage** возвращает строку для всех четырех сочетаний входящего и исходящего направления, а также внешних и внутренних классов следующим образом:  
  
|time|database_name|direction|class|time_period|quantity|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Ingress|External|Peak|66|  
|2012-04-21 17:00:00|Db1|Egress|External|Peak|741|  
|2012-04-21 17:00:00|Db1|Ingress|Internal|Пик|1052|  
|2012-04-21 17:00:00|Db1|Egress|Внутренние|Peak|3525|  
  
### <a name="interpreting-data-direction-for-includessgeodrincludesssgeodr-mdmd"></a>Интерпретация направления данных для [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]  
 Для [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] сведения об использовании полосы пропускания отображаются в логической базе данных master с обеих сторон связи непрерывного копирования. Поэтому необходимо интерпретировать индикаторы исходящего и входящего направления с точки зрения логического сервера, к которому направлен запрос. Например, рассмотрим поток репликации, который перемещает 1 МБ данных с исходного сервера на целевой сервер. В этом случае на исходном сервере 1 МБ учитывается в общем объеме отправленных данных, а на целевом сервере 1 МБ записывается как полученные данные.  
  
> [!NOTE]  
>  Данные передаются с исходного сервера на целевой сервер в направлении потока данных пользователя. Однако некоторые данные требуется передавать и в другом направлении.  
  
  
