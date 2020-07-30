---
title: srv_willconvert (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
description: Узнайте, как srv_willconvert определяет, доступно ли преобразование определенного типа данных в библиотеке ODS.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_willconvert
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: ef515b200221a6bb439a65a02e546017046dd0e4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248236"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a>srv_willconvert (API-интерфейс расширенных хранимых процедур)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Определяет, доступно ли конкретное преобразование типов данных в библиотеке ODS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srctype*  
 Указывает тип преобразуемых данных. Этот параметр может иметь любой из типов данных API-интерфейса расширенных хранимых процедур.  
  
 *desttype*  
 Указывает тип данных, в который преобразуются исходные данные. Этот параметр может иметь любой из типов данных API-интерфейса расширенных хранимых процедур.  
  
## <a name="returns"></a>Результаты  
 Значение TRUE, если преобразование типов данных поддерживается, значение FALSE, если преобразование типов данных не поддерживается.  
  
## <a name="remarks"></a>Remarks  
 Описание каждого типа данных см. в разделе [Типы данных (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://www.microsoft.com/msrc?rtc=1).  
  
## <a name="see-also"></a>См. также:  
 [srv_convert (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-convert-extended-stored-procedure-api.md)  
  
  
