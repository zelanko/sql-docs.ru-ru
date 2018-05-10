---
title: '@@OPTIONS (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9c36f69481c79f01f4ad6dcebf111f3d787fc57e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="x40x40options-transact-sql"></a>&#x40;&#x40;OPTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о текущих параметрах инструкции SET.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@OPTIONS  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Параметры могут быть получены при использовании команды **SET** или из значения **sp_configure user options**. Значения сеанса, настроенные командой **SET**, переопределяют параметры **sp_configure**. Многие средства (такие как [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] автоматически настраивают набор параметров. Каждый пользователь имеет функцию @@OPTIONS, представляющую конфигурацию.  
  
 Вы можете изменить язык и параметры обработки запроса для определенного сеанса пользователя, используя выражение SET.  **@@OPTIONS** обнаруживает только параметры, для которых заданы значения ON или OFF.  
  
 Функция **@@OPTIONS** возвращает битовую матрицу параметров, преобразованную в десятичное целое число. Битовые параметры хранятся в местах, описанных в таблице в статье [Настройка параметра конфигурации сервера user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md).  
  
 Для декодирования значения **@@OPTIONS** преобразуйте целое число, возвращенное **@@OPTIONS**, в двоичное, затем найдите значения в таблице в статье [Настройка параметра конфигурации сервера user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md). Например, если `SELECT @@OPTIONS;` возвращает значение `5496`, используйте калькулятор Windows в режиме "Программист" (**calc.exe**) для преобразования десятичного значения `5496` в двоичное. Результат `1010101111000`. Самые правые символы (двоичные 1, 2 и 4) — нули. Это означает, что первые три элемента в таблице отключены. Если обратиться к таблице, можно увидеть, что это параметры **DISABLE_DEF_CNST_CHK**, **IMPLICIT_TRANSACTIONS** и **CURSOR_CLOSE_ON_COMMIT**. Следующий элемент (**ANSI_WARNINGS** в позиции `1000`) включен. Продолжайте двигаться влево по битовой матрице и вниз по списку параметров. Если самые левые символы — нули, они усекаются при преобразовании типа. Битовая карта `1010101111000` фактически является `001010101111000` для представления всех 15 параметров.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-demonstration-of-how-changes-affect-behavior"></a>A. Пример того, как изменения влияют на поведение  
 В приведенном ниже примере демонстрируется разница в том, как производится объединение при двух разных настройках параметра **CONCAT_NULL_YIELDS_NULL**.  
  
```  
SELECT @@OPTIONS AS OriginalOptionsValue;  
SET CONCAT_NULL_YIELDS_NULL OFF;  
SELECT 'abc' + NULL AS ResultWhen_OFF, @@OPTIONS AS OptionsValueWhen_OFF;  
  
SET CONCAT_NULL_YIELDS_NULL ON;  
SELECT 'abc' + NULL AS ResultWhen_ON, @@OPTIONS AS OptionsValueWhen_ON;  
```  
  
### <a name="b-testing-a-client-nocount-setting"></a>Б. Проверка настройки NOCOUNT клиента  
 В приведенном ниже примере задается аргумент `NOCOUNT``ON`, а затем проверяется значение `@@OPTIONS`. Параметр `NOCOUNT``ON` препятствует тому, чтобы сообщение о количестве обработанных строк отправлялось обратно клиенту при выполнении каждой инструкции в сеансе. Функции `@@OPTIONS` присваивается значение `512` (0x0200). Оно представляет аргумент NOCOUNT. В этом примере производится проверка того, задействован ли аргумент NOCOUNT у клиента. Например, он может помочь отследить отличия в производительности у клиента.  
  
```  
SET NOCOUNT ON  
IF @@OPTIONS & 512 > 0   
RAISERROR ('Current user has SET NOCOUNT turned on.', 1, 1)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Настройка параметра конфигурации сервера «user options»](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)  
  
  
