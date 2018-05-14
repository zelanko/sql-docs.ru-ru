---
title: Командлет Get-PowerPivotSystemService | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c2a955a9d9b91521adc6abfcdd5af4109958fa8f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="get-powerpivotsystemservice-cmdlet"></a>Командлет «Get-PowerPivotSystemService»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Возвращает глобальные свойства объекта системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. 

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
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
  
  
