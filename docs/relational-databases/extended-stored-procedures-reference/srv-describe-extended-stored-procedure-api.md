---
title: "srv_describe (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_describe
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_describe
ms.assetid: 2115600e-5ce7-4be0-9cd3-a1dd1fab0729
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f71e57149aeb7f07c3edfd7c69806b71c3272b50
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="srvdescribe-extended-stored-procedure-api"></a>srv_describe (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Задает имя столбца, исходный и целевой типы данных для конкретного столбца в строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_describe (  
SRV_PROC *  
srvproc  
,  
int  
colnumber  
,  
DBCHAR *  
column_name  
,  
int  
namelen  
,  
DBINT  
desttype  
,  
DBINT  
destlen  
,  
DBINT  
srctype  
,  
DBINT  
srclen  
,  
void *  
srcdata  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор для конкретного клиентского соединения (в данном случае подразумевается клиент, который отправил строку). В этой структуре содержатся все сведения, которые библиотека API-интерфейса расширенных хранимых процедур использует для управления обменом данными между приложением и клиентом.  
  
 *colnumber*  
 Не поддерживается в текущей версии. Столбцы должны быть описаны по порядку. Все столбцы должны быть описаны до вызова **srv_sendrow**.  
  
 *column_name*  
 Задает имя столбца, к которому принадлежат данные. Этот параметр может иметь значение NULL, поскольку столбец не обязательно должен иметь имя.  
  
 *namelen*  
 Задает длину *column_name* в байтах. Если значение аргумента *namelen* равно SRV_NULLTERM, то значение аргумента *column_name* должно оканчиваться нулевым символом.  
  
 *desttype*  
 Задает тип данных столбца строки назначения. Это — тип данных, передаваемых клиенту. Тип данных нужно задавать, даже если данные имеют значение NULL. Дополнительные сведения см. в разделе [Типы данных (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
 *destlen*  
 Задает длину данных (в байтах), которые должны быть переданы клиенту. Для типов данных фиксированной длины, не допускающих значений NULL, параметр *destlen* не учитывается. Для типов данных с переменной длиной и типов данных с фиксированной длиной, поддерживающих значения NULL, параметр *destlen* задает максимальную длину целевых данных.  
  
 *srctype*  
 Задает тип исходных данных.  
  
 *srclen*  
 Задает длину исходных данных в байтах. Для типов данных с фиксированной длиной это значение не учитывается.  
  
 *srcdata*  
 Предоставляет адрес исходных данных для конкретного столбца. Функция **srv_sendrow** после вызова ищет данные для параметра *colnumber* в параметре *srcdata*. Следовательно, этот параметр нельзя освобождать до вызова функции **srv_sendrow**. Адрес исходных данных можно изменить между вызовами функции **srv_sendrow** с помощью вызова функции **srv_setcoldata**. Память, выделенная для *srcdata*, не должна освобождаться до замены данных столбца с помощью еще одного вызова метода **srv_setcoldata** или **srv_senddone**.  
  
 Если значение параметра *desttype* равно SRVDECIMAL или SRVNUMERIC, параметр *srcdata* должен быть указателем на структуру типа DBNUMERIC или DBDECIMAL, в которой полям точности и масштаба уже присвоены требуемые значения. Параметр DEFAULTPRECISION позволяет задать точность по умолчанию, а параметр DEFAULTSCALE — масштаб по умолчанию.  
  
## <a name="returns"></a>Возвращает  
 Порядковый номер описываемого столбца. Первый столбец имеет номер 1. При возникновении ошибки возвращается 0.  
  
## <a name="remarks"></a>Замечания  
 Функция **srv_describe** должна быть вызвана по одному разу для каждого столбца данной строки перед первым вызовом функции **srv_sendrow**. Столбцы в строке могут быть описаны в любом порядке.  
  
 Для изменения местонахождения и длины исходных данных в строках столбцов до передачи полного результирующего набора можно использовать функции **srv_setcoldata** и **srv_setcollen**, соответственно.  
  
 Описание типов данных и преобразований типов данных API-интерфейса расширенных хранимых процедур см. в разделе [Типы данных (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md).  
  
 Если имя столбца в приложении задано в Юникоде, то перед вызовом функции **srv_describe** его нужно перевести в многобайтовую кодировку, заданную на сервере. Дополнительные сведения см. в статье [Данные в Юникоде и кодовые страницы сервера](../../relational-databases/extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [srv_sendrow (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-sendrow-extended-stored-procedure-api.md)   
 [srv_setutype (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-setutype-extended-stored-procedure-api.md)   
 [srv_setcoldata (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-setcoldata-extended-stored-procedure-api.md)  
  
  
