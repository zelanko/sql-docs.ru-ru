---
title: Командлет remove-PowerPivotSystemServiceInstance | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c3f6f960d0f2b39fa877203ede26f5e66b5c3c37
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="remove-powerpivotsystemserviceinstance-cmdlet"></a>Командлет «Remove-PowerPivotSystemServiceInstance»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Удаляет экземпляр системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из фермы.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
 Командлет Remove-PowerPivotSystemServiceInstance удаляет сведения об экземпляре системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из фермы. Не удаляет программные файлы. Чтобы удалить программные файлы, нужно отменить их установку.  
  
 При удалении системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] не забудьте выполнить командлет Remove-PowerPivotEngineServiceInstance, чтобы удалить связанный экземпляр служб Analysis Services, а затем командлет Remove-PowerPivotServiceApplication, чтобы удалить все приложения службы PowerPivot. Приложения службы больше не будут работать после удаления служб.  
  
 Чтобы отменить это изменение, можно выполнить команду New-PowerPivotSystemServiceInstance -Provision:$true и заново включить сведения об экземпляре.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>-Identity \<PowerPivotMidTierServiceInstancePipeBind >  
 Указывает идентификатор GUID экземпляра системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , который необходимо удалить. На каждом сервере приложений, где установлена надстройка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, имеется один экземпляр службы.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-deletelocal-switch"></a>-DeleteLocal \<переключения >  
 Удаляет экземпляр системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , установленный на локальном компьютере, после чего можно удалить экземпляр без указания удостоверения объекта.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-confirm-switch"></a>-Подтверждение \<переключения >  
 Выводит приглашение для подтверждения перед выполнением команды. Это значение включено по умолчанию. Чтобы исключить подтверждения в команде, укажите параметр Confirm:$ false.  
  
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
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 В этом примере показано, как удалить экземпляр системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , работающий на локальном сервере приложений.  
  
## <a name="example-2"></a>Пример 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 В этом примере показано, как удалить конкретную системную службу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на основе ее удостоверения.  
  
  
