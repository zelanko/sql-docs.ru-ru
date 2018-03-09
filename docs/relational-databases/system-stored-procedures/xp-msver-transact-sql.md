---
title: "xp_msver (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs: TSQL
helpviewer_keywords: xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57509a7787087d747ae84f0bed6c67e8e3cd0f67
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="xpmsver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **xp_msver** также возвращает сведения о номере действительной компоновки сервера и сведения о среде сервера. Сведения, **xp_msver** возвращает могут использоваться в [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, пакеты, хранимые процедуры и т. д., чтобы усовершенствовать логику не зависящего от платформы кода.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *optname*  
 Имя параметра может иметь одно из следующих значений.  
  
|Имя параметра/столбца|Description|  
|-------------------------|-----------------|  
|**ProductName**|Название продукта; например [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProductVersion**|Номер версии продукта.|  
|**Язык**|Языковая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Платформа**|Имя операционной системы, имя производителя и имя семейства чипов для компьютера, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Комментарии**|Различные сведения об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Название организации**|Имя компании, производящей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; например [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**FileDescription**|Операционная система.|  
|**Необязательный параметр**|Версия исполняемого файла [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Внутреннееимя**|[!INCLUDE[msCoName](../../includes/msconame-md.md)]внутреннее имя для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например SQLSERVR.|  
|**LegalCopyright**|Сведения о законных авторских правах, требуемые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например © [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corp. 1988-2005.|  
|**LegalTrademarks**|Сведения о зарегистрированном товарном знаке, требуемые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например [!INCLUDE[msCoName](../../includes/msconame-md.md)] является зарегистрированным товарным знаком [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**OriginalFilename**|Имя файла, выполняемого при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; например Sqlservr.exe.|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**WindowsVersion**|Версия [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, установленная на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProcessorCount**|Количество процессоров в компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProcessorActiveMask**|Показывает запущенные и пригодные к использованию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows процессоры, установленные в компьютере, на котором работает [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|**ProcessorType**|Тип процессора. Аналогично **платформы**.|  
|**PhysicalMemory**|Количество памяти RAM в мегабайтах (МБ), установленной на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Идентификатор продукта**|Идентификационный номер продукта (PID). Указывается в процессе установки. Этот номер расположен на наклейке на подлинной коробке с дисками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 1 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 **xp_msver**, без указания аргументов возвращает четыре столбца результирующий набор, содержащий все значения параметров. **xp_msver**, для любого параметра возвращает четыре столбца результирующего набора со значениями для этого параметра.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
