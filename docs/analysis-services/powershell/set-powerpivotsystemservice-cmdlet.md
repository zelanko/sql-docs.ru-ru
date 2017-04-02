---
title: "Командлет &#171;Set-PowerPivotSystemService&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f6ef197b-3d74-4339-ae73-8a7c1eaf0e91
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Командлет &#171;Set-PowerPivotSystemService&#187;
  Задает глобальные свойства объекта PowerPivotSystemService на уровне фермы.  
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## Синтаксис  
  
```  
Set-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [-UpdateAssemblyInformation <switch>] [-WorkbookUpgradeOnDataRefresh <boolean>] [-DirectTCPConnections <boolean>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 Командлет Set-PowerPivotSystemService обновляет свойства родительского объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  
  
## Параметры  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Указывает родительский объект, для которого выполняется обновление свойств. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### -UpdateAssemblyInformation \<switch>  
 Используется только для обновления. Если версия сборки, развернутой в ферме, отличается от версии, хранимой в базе данных конфигурации SharePoint, запустите этот командлет, чтобы обновить сведения о сборке в базе данных конфигурации. Сведения о версии сборки доступны в свойствах файла Microsoft.AnalysisServices.SharePoint.Integration.dll, который хранится в глобальной сборке.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -WorkbookUpgradeOnDataRefresh \<boolean>  
 Используется для автоматического обновления книги [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] в начале запланированного обновления данных на сервере. Обновление данных поддерживается только для книг, соответствующих текущей версии сервера. Если включить это свойство, книга будет автоматически обновляться, поэтому обновление данных можно будет продолжать. Это свойство задается на уровне экземпляра сервера. Оно не может отличаться для конкретных книг, библиотек, сайтов или пользователей.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|2|  
|Значение по умолчанию|false|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -DirectTCPConnections \<boolean>  
 Указывает, что службы Excel Services отправляют все запросы напрямую экземпляру служб SQL Server Analysis Services (POWERPIVOT), который загрузил базу данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Это делается в обход поставщика данных MSOLAP и транспорта канала, используемых для каждого запроса, отправляемого базе данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Этот параметр улучшает производительность и масштабируемость запросов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], оптимизируя подключение к загруженным базам данных. Обратите внимание, что этот параметр не изменяет поведение изначального распределения запроса загрузки. Другие параметры, такие как –RoundRobinAllocation и –HealthBasedAllocation, используемые для распределения запросов загрузки баз данных среди нескольких экземпляров [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint в ферме, остаются незатронутыми, так как параметр –DirectTCPConnections применяется только к запросам, которые отправляются после загрузки базы данных.  
  
 Для топологий ферм, которые включают службы Excel Services и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, работающие на разных серверах приложений, следует открыть порт в брандмауэре, чтобы запросы достигали экземпляра служб SQL Server Analysis Services (POWERPIVOT). Инструкции о том, как включить входящие соединения для именованного экземпляра служб Analysis Services, см. в разделе [Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|3|  
|Значение по умолчанию|false|  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### -Confirm \<switch>  
 Выводит приглашение для подтверждения перед выполнением команды. Это значение включено по умолчанию. Чтобы исключить подтверждения в команде, укажите параметр Confirm:$ false.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### \<Общие параметры>  
 Этот командлет поддерживает общие параметры: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer и OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
## Пример 1  
  
```  
C:\PS>Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true  
```  
  
 Включает автоматическое обновление книг предыдущих версий, чтобы можно было продолжить обновление данных по расписанию.  
  
  