---
title: "Командлет Get-PowerPivotSystemService | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 20c13c68abadafcbe4cc357345a4b3ba7d0668f7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="get-powerpivotsystemservice-cmdlet"></a>Командлет «Get-PowerPivotSystemService»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Возвращает глобальные свойства [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] объекта системной службы в ферме. 

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Командлет Get-PowerPivotSystemService возвращает глобальные свойства объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Может быть только один родительский объект на ферму, однако каждая ферма может иметь несколько экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , работающих на разных серверах приложений в ферме. Родительский объект отображает параметры на уровне фермы, которые не зависят от экземпляра. Если ферма включает несколько экземпляров [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, разделенный запятыми список экземпляров покажет, сколько экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] есть в ферме.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-identity-powerpivotmidtierservicepipebind"></a>-Identity \<PowerPivotMidTierServicePipeBind >  
 Указывает возвращаемый родительский объект. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
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
C:\PS>Get-PowerPivotSystemService  
```  
  
 В этом примере возвращаются глобальные свойства родительского объекта, при этом отображаются свойства, которые являются общими для всех экземпляров системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  
  
  
