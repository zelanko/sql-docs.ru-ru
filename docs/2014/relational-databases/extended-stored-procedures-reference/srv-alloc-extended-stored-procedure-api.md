---
title: srv_alloc (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9c821df66c6599dd3e7e3fecdff637d250f965c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096418"
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (API-интерфейс расширенных хранимых процедур)
    
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
  
## <a name="returns"></a>Возвращает  
 Указатель на распределенную память. Если объем памяти, указываемый аргументом *size*, выделить не удалось, возвращается указатель NULL.  
  
## <a name="remarks"></a>Примечания  
 Функция **srv_alloc** является эквивалентом функции [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API **GlobalAlloc**. Обычные функции управления памятью библиотеки времени выполнения Windows API на языке C могут использоваться в приложении API-интерфейса расширенных хранимых процедур.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  