---
title: Командлет Update-PowerPivotSystemService | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c7b99c58d4051aef4e92c45c9d7b57537f97ed40
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="update-powerpivotsystemservice-cmdlet"></a>Командлет «Update-PowerPivotSystemService»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Обновляет родительский объект системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
 Командлет **Update-PowerPivotSystemService** выполняет ряд операций обновления применительно к родительскому объекту системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , экземплярам и приложениям службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Все службы и приложения среднего уровня в развертывании [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint должны работать на одном функциональном уровне. Этот командлет выполняет действия обновления для всех таких объектов.  
  
 Запустите этот командлет после выполнения программы установки SQL Server для установки новой версии [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или применения накопительного обновления к серверу. Для проверки того, была ли операция обновления успешной, выполните `Get-PowerPivotSystemService` для определения значения свойства **NeedsUpgrade** . Если свойство **NeedsUpgrade** имеет значение true, необходимо выполнить указанный командлет для обновления объектов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] промежуточного уровня в ферме.  
  
 Развертывание [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint включает службы данных промежуточного уровня и уровня сервера, поэтому необходимо выполнять командлет **Update-PowerPivotEngineService** каждый раз после выполнения командлета **Update-PowerPivotSystemService** , чтобы гарантировать использование одной и той же версии на обоих уровнях в ферме.  
  
 Обновление не может быть отменено до предыдущей версии. Если требуется вернуться к предыдущей версии, удалите [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из фермы SharePoint и установите заново. Для проверки того, была ли операция обновления успешной, выполните `Get-PowerPivotSystemService` для определения глобальных свойств, относящихся к информации о версии, и проверки того, что свойство **NeedsUpgrade** больше не имеет значение true.  
  
## <a name="parameters"></a>Параметры  
  
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
 Этот командлет поддерживает следующие параметры:  
  
-   Подробный  
  
-   Отладка  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
  
