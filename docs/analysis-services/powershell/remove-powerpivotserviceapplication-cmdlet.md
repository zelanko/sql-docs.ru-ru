---
title: Командлет remove-PowerPivotServiceApplication | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ddd179e82dc7c0170e99ece2a8018c0a8454c11d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="remove-powerpivotserviceapplication-cmdlet"></a>Командлет «Remove-PowerPivotServiceApplication»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Удаляет приложение службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Remove-PowerPivotServiceApplication [-Identity <SPGeminiServiceApplicationPipeBind>] [-DeleteAll <switch>] [-RemoveData <switch>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
 Командлет Remove-PowerPivotServiceApplication удаляет из фермы приложение службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Для одновременного удаления всех приложений службы используйте команду DeleteAll, для удаления одного экземпляра — параметр Identity. Чтобы получить сведения об экземпляре, выполните командлет Get-PowerPivotServiceApplication, чтобы получить все экземпляры в ферме.  
  
 Параметр RemoveData используется при необходимости удалить базы данных приложения службы и кэшированные файлы. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] при удалении приложения службы книги остаются в библиотеках содержимого, но не используются.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Указывает идентификатор GUID приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Если необходимо удалить только одно приложение, оставив другие приложения службы без изменений, следует указать идентификатор GUID.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|0|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|true|  
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
  
### <a name="-deleteall-switch"></a>-DeleteAll \<переключения >  
 Удаляет все приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , но не удаляет базу данных приложений службы и объекты экземпляров службы в ферме. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] При удалении приложений служб объекты системной службы и службы ядра [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] остаются созданными, но их уже нельзя использовать.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="-removedata-switch"></a>-RemoveData \<переключения >  
 Удаляет базу данных приложения службы, которая содержит расписания обновления данных, данные об использовании книг, карты экземпляров, которые используются для отслеживания того, какие базы данных загружены, и другие внутренние сведения.  
  
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
C:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop  
```  
  
 В этом примере удаляется приложение службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , но не удаляется его база данных и кэш. Если не указать удостоверение, появится подсказка о том, что его необходимо указать.  
  
## <a name="example-2"></a>Пример 2  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -DeleteAll  
```  
  
 В этом примере удаляются все приложения службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Базы данных и кэш не удаляются.  
  
## <a name="example-3"></a>Пример 3  
  
```  
CC:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop -RemoveData  
```  
  
 В этом примере удаляется одно приложение службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , а также его база данных и файлы кэша.  
  
  
