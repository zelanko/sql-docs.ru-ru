---
title: "Командлет Get-PowerPivotServiceApplication | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b171a1fe3be824954af612d19251f9f45729c063
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Командлет «Get-PowerPivotServiceApplication»

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Возвращает одно или несколько приложений службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Командлет Get-PowerPivotServiceApplication возвращает приложение службы, указанное параметром Identity. Если параметр не указан, командлет возвращает все приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Каждое приложение идентифицируется отображаемым именем, типом и идентификатором GUID. Для просмотра дополнительных свойств приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] добавьте в командлет параметр format-list.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Указывает возвращаемое приложение службы. Это значение должно быть допустимым идентификатором GUID, уникальным образом идентифицирующим объект в ферме.  
  
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
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 В этом примере возвращается одно или несколько приложений службы в ферме.  
  
## <a name="example-2"></a>Пример 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 Этот пример возвращает все свойства приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="example-3"></a>Пример 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 В этом примере возвращается одно приложение службы, при этом отображается его имя, тип и идентификатор GUID. Если отображаемое имя слишком длинное, оно будет усечено. Для просмотра полного имени воспользуйтесь параметром format-list.  
  
  
