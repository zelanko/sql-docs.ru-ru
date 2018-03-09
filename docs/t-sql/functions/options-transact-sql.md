---
title: "@@OPTIONS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@OPTIONS'
- '@@OPTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, current SET options
- '@@OPTIONS function'
- current SET options
ms.assetid: 3d5c7f6e-157b-4231-bbb4-4645a11078b3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75919b6d27b2a81a9aba3575d3a9f3c54f0e0850
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40options-transact-sql"></a>&#x40;&#x40;параметры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о текущих параметрах инструкции SET.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@OPTIONS  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Замечания  
 Параметры могут быть результатом использования **ЗАДАТЬ** команды или из **параметры пользователя хранимой процедуры sp_configure** значение. Значения сеанса, настроенные **ЗАДАТЬ** переопределение команда **sp_configure** параметры. Многие средства (такие как [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] автоматически настраивают набор параметров. Каждый пользователь имеет @@OPTIONS функция, представляющая конфигурацию.  
  
 Вы можете изменить язык и параметры обработки запроса для определенного сеанса пользователя, используя выражение SET.  **@@OPTIONS**  обнаруживает только параметры, которые установлены в значение ON или OFF.  
  
 **@@OPTIONS**  Функция возвращает растровое Отображение параметров, конвертированных систему базового целого числа 10 (десятичная). Настройки бита хранятся в местах, описанных в таблице в разделе [Настройка параметра конфигурации сервера user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md).  
  
 Декодируемая **@@OPTIONS**  , конвертируйте целое число, возвращенное **@@OPTIONS**  в двоичный формат, а затем посмотрите значения в таблице в [настройте параметры пользователей сервера Параметр конфигурации](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md). Например если `SELECT @@OPTIONS;` возвращает значение `5496`, используйте программный калькулятор Windows (**calc.exe**) для преобразования десятичных `5496` в двоичный формат. Результат `1010101111000`. Правый большинство символов (двоичные 1, 2 и 4) равняются 0, означает, что первые три элемента в таблице, отключены. Таблице, вы видите правильность **DISABLE_DEF_CNST_CHK** и **IMPLICIT_TRANSACTIONS**, и **CURSOR_CLOSE_ON_COMMIT**. Следующий элемент (**ANSI_WARNINGS** в `1000` позиции) включен. Продолжить работу слева хотя Битовая карта и вниз в списке параметров. Если параметры слева, 0, они усекаются преобразования типов. Битовая карта `1010101111000` фактически является `001010101111000` для представления всех 15 параметров.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-demonstration-of-how-changes-affect-behavior"></a>A. Пример того, как изменения влияют на поведение  
 В следующем примере показано различие в поведении при конкатенации с двумя разными настройками параметра **CONCAT_NULL_YIELDS_NULL** параметр.  
  
```  
SELECT @@OPTIONS AS OriginalOptionsValue;  
SET CONCAT_NULL_YIELDS_NULL OFF;  
SELECT 'abc' + NULL AS ResultWhen_OFF, @@OPTIONS AS OptionsValueWhen_OFF;  
  
SET CONCAT_NULL_YIELDS_NULL ON;  
SELECT 'abc' + NULL AS ResultWhen_ON, @@OPTIONS AS OptionsValueWhen_ON;  
```  
  
### <a name="b-testing-a-client-nocount-setting"></a>Б. Проверка настройки NOCOUNT клиента  
 В следующем примере задается `NOCOUNT``ON` , а затем проверяется значение `@@OPTIONS`. `NOCOUNT``ON` Отменяет сообщение о количестве строк, затронутых отправку запрашивающему клиенту при выполнении каждой инструкции в сеансе. Функции `@@OPTIONS` присваивается значение `512` (0x0200). Оно представляет аргумент NOCOUNT. В этом примере производится проверка того, задействован ли аргумент NOCOUNT у клиента. Например, он может помочь отследить отличия в производительности у клиента.  
  
```  
SET NOCOUNT ON  
IF @@OPTIONS & 512 > 0   
RAISERROR ('Current user has SET NOCOUNT turned on.', 1, 1)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Настройка параметра конфигурации сервера «user options»](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)  
  
  
