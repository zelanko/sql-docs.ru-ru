---
title: srv_alloc (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
ms.openlocfilehash: 729675f7df3a4e394bb28f4074644289489ef248
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050795"
---
# <a name="srv_alloc-extended-stored-procedure-api"></a>srv_alloc (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Динамически распределяет память.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *size*  
 Указывает число байтов для распределения.  
  
## <a name="returns"></a>Возвращаемое значение  
 Указатель на распределенную память. Если объем памяти, указываемый аргументом *size*, выделить не удалось, возвращается указатель NULL.  
  
## <a name="remarks"></a>Remarks  
 Функция **srv_alloc** является эквивалентом функции [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API **GlobalAlloc**. Обычные функции управления памятью библиотеки времени выполнения Windows API на языке C могут использоваться в приложении API-интерфейса расширенных хранимых процедур.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
