---
title: Командлет Get-PowerPivotServiceApplication | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71fb05a62dab5ec224744df9425e06cf23c16397
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Командлет «Get-PowerPivotServiceApplication»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Возвращает одно или несколько приложений службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
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
  
  
