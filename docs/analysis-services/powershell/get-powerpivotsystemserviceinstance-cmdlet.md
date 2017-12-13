---
title: "Командлет Get-PowerPivotSystemServiceInstance | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56027a8e-1949-4349-b616-68c8b1d2963c
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2e52176bc32adbaee46a22d3c4df6a331cf7c39b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="get-powerpivotsystemserviceinstance-cmdlet"></a>Командлет «Get-PowerPivotSystemServiceInstance»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Возвращает один или несколько экземпляров [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] системной службы, работающих на серверах приложений в ферме.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Командлет Get-PowerPivotSystemServiceInstance возвращает свойства одного или нескольких экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , работающих в ферме. Командлет сообщает тип приложения, состояние (в сети или вне сети) и удостоверение. Для просмотра дополнительных свойств определенного экземпляра добавьте в командлет параметры Identity и format-list.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>-Identity \<PowerPivotMidTierServiceInstancePipeBind >  
 Указывает возвращаемый экземпляр служб. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает общие параметры: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer и OutVariable. Дополнительные сведения см. в разделе [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
## <a name="example-1"></a>Пример 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 В этом примере возвращаются дополнительные свойства указанного экземпляра, включая имя сервера, версию и состояние обновления.  
  
  
