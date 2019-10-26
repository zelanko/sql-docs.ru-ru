---
title: sys. sp_cdc_cleanup_change_table (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_cleanup_change_table
- sp_cdc_cleanup_change_table_TSQL
- sys.sp_cdc_cleanup_change_table
- sys.sp_cdc_cleanup_change_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_cleanup_change_tables
- sp_cdc_cleanup_change_tables
ms.assetid: 02295794-397d-4445-a3e3-971b25e7068d
author: rothja
ms.author: jroth
ms.openlocfilehash: 51c0af34fb3158cc5032ee9ef53abce22d8ecc3a
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909331"
---
# <a name="syssp_cdc_cleanup_change_table-transact-sql"></a>sys.sp_cdc_cleanup_change_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет строки из таблицы изменений в текущей базе данных на основе указанного значения *low_water_mark* . Данная хранимая процедура используется для прямого управления процессом очистки таблицы изменений. Данную процедуру необходимо использовать с большой осторожностью, так как ее выполнение затрагивает всех потребителей данных таблицы изменений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_cleanup_change_table   
  [ @capture_instance = ] 'capture_instance',   
  [ @low_water_mark = ] low_water_mark ,  
  [ @threshold = ]'delete threshold'  
```  
  
## <a name="arguments"></a>Аргументы  
 [@capture_instance =] "*capture_instance*"  
 Имя экземпляра системы отслеживания, связанного с таблицей изменений. *capture_instance* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
 *capture_instance* должен присвоить имя экземпляру отслеживания, который существует в текущей базе данных.  
  
 [@low_water_mark =] *low_water_mark*  
 Регистрационный номер транзакции в журнале (LSN), который будет использоваться в качестве нового нижнего предела для *экземпляра отслеживания*. *low_water_mark* является **двоичным (10)** и не имеет значения по умолчанию.  
  
 Если значение не равно null, оно должно выглядеть как значение start_lsn текущей записи в таблице [CDC. LSN _time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) . Если в таблице cdc.lsn_time_mapping есть несколько записей, соответствующих одному моменту времени, на который ссылается указатель новой нижней конечной точки, то данному указателю присваивается наименьшее значение номера LSN данной группы записей.  
  
 Если значение явно задано как NULL, то текущая *Нижняя* граница для *экземпляра отслеживания* используется для определения верхней границы операции очистки.  
  
 [@threshold=] "*удалить порог*"  
 Максимальное число записей, подлежащих удалению, которые могут быть удалены с помощью одной инструкции при очистке. *delete_threshold* имеет тип **bigint**и значение по умолчанию 5000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Remarks  
 Процедура sys.sp_cdc_cleanup_change_table производит следующие операции.  
  
1.  Если параметр @low_water_mark не равен NULL, он устанавливает для *экземпляра системы отслеживания* значение start_lsn, равное новому *нижнему пределу*.  
  
    > [!NOTE]  
    >  Новая нижняя конечная точка может не являться точкой, указанной в вызове хранимой процедуры. Если в таблице cdc.lsn_time_mapping есть несколько записей, соответствующих одному моменту времени, то в качестве нижней конечной точки выбирается наименьшее значение start_lsn в группе записей. Если параметр @low_water_mark имеет значение NULL или текущий нижний предел больше, чем новый ловватермарк, значение start_lsn для экземпляра отслеживания остается неизменным.  
  
2.  Записи таблицы изменений, значения __$start_lsn которых меньше нижней конечной точки, удаляются. Пороговое значение удаления используется для ограничения количества строк, удаляемых в одной транзакции. Неуспешное удаление записей сопровождается выводом сообщения, но не влияет на изменения нижней конечной точки экземпляра системы отслеживания, которая могла быть создана при вызове.  

 Пользуйтесь процедурой sys.sp_cdc_cleanup_change_table в следующих случаях.  
  
-   Задание агента очистки сообщает о неудачном удалении.  
  
     Администратор может запустить данную хранимую процедуру явным образом, чтобы повторно выполнить эту операцию. Чтобы повторить очистку для данного экземпляра отслеживания, выполните хранимую процедуру sys. sp_cdc_cleanup_change_table и укажите значение NULL для параметра @low_water_mark.  
  
-   Простая политика на основе срока хранения, используемая заданием агента очистки, не является оптимальной.  
  
     Поскольку эта хранимая процедура выполняет очистку для одного экземпляра системы отслеживания, то она может быть использована для построения пользовательской стратегии очистки, которая применяет правила очистки к индивидуальному экземпляру системы отслеживания.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также статью  
  [CDC.&#60;fn_cdc_get_all_changes_&#62;&#40;capture_instance Transact-&#41; SQL  ](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
 [sys. fn_cdc_get_min_lsn &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys. fn_cdc_increment_lsn &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)  
  
  
