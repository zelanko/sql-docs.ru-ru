---
title: sp_xml_removedocument (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xml_removedocument_TSQL
- sp_xml_removedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_removedocument
ms.assetid: f9dca50a-8baf-4170-90bc-e72783ce5b73
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5f249871fd1037ad5fcf485c85e7b758e9becf7a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65979975"
---
# <a name="spxmlremovedocument-transact-sql"></a>sp_xml_removedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет встроенное представление XML-документа, заданного дескриптором документа и делает недействительным дескриптор документа.  
  
> [!NOTE]  
>  Проанализированный документ хранится во внутреннем кэше [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Средство синтаксического анализа MSXML (Msxmlsql.dll) использует восьмую часть всей памяти, доступной для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы избежать нехватки памяти, выполните **sp_xml_removedocument** чтобы освободить занятую память.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_xml_removedocument hdoc  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdoc*  
 Дескриптор только что созданного документа. Неправильный дескриптор возвращает ошибку. *hdoc* должно быть целым числом.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или > 0 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример удаляет встроенное представление XML-документа. Переданный на вход дескриптор документа.  
  
```  
EXEC sp_xml_removedocument @hdoc;  
```  
  
## <a name="see-also"></a>См. также      
 <br>[Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[XML хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[sys.dm_exec_xml_handles (Transact-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_preparedocument(Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
  
  
