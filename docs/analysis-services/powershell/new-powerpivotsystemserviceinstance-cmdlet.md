---
title: "Командлет New-PowerPivotSystemServiceInstance | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7ea94113-c0f1-4cca-9228-f1a034fba5db
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8cde819f27942e78bf67c85356602ad1954420c0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="new-powerpivotsystemserviceinstance-cmdlet"></a>Командлет «New-PowerPivotSystemServiceInstance»

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Добавляет новый экземпляр системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сервер приложений.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Командлет New-PowerPivotSystemServiceInstance подготавливает новый объект PowerPivotSystemService на уровне фермы после того, как вы установили [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint на локальном сервере приложений с помощью программы установки SQL Server. На каждом сервере приложений можно указать только один экземпляр службы.  Если служба уже указана, выполнить этот командлет нельзя.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-parentservice-powerpivotmidtierservicepipebind"></a>-ParentService \<PowerPivotMidTierServicePipeBind >  
 Указывает идентификатор GUID родительского объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. В этом выпуске допускается только один родительский объект. Команда Get-PowerPivotSystemService используется для получения объекта службы или его идентификатора GUID.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-systemserviceinstancename-string"></a>-SystemServiceInstanceName \<строка >  
 Указывает имя, идентифицирующее этот объект.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|1|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="provision-switchparameter"></a>Подготовка к работе [\<SwitchParameter >]  
 Делает службу доступной на SharePoint. Допустимые значения — $true или $false.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer и OutVariable. Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
## <a name="example-1"></a>Пример 1  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 В этом примере показана наиболее распространенная форма командлета. Командлет регистрирует в ферме системную службу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на локальном сервере приложений.  
  
## <a name="example-2"></a>Пример 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 В этом примере задается имя для экземпляра системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] без его подготовки. Если имя не задано, будет использовано имя по умолчанию — экземпляр системной службы служб SQL Server Analysis Services. Создание пользовательского имени для службы не является обязательным. Службу можно именовать для поддержки сценариев проверки, либо если имеется пользовательское средство или скрипт, который провизионирует экземпляр на последующих этапах.  
  
  

