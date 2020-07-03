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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ac10ff9accd4cac39caef8139406319701026e79
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891170"
---
# <a name="syssp_cdc_cleanup_change_table-transact-sql"></a>sys.sp_cdc_cleanup_change_table (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
 [ @capture_instance =] "*capture_instance*"  
 Имя экземпляра системы отслеживания, связанного с таблицей изменений. Аргумент *capture_instance* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
 *capture_instance* должен присвоить имя экземпляру отслеживания, который существует в текущей базе данных.  
  
 [ @low_water_mark =] *low_water_mark*  
 Регистрационный номер транзакции в журнале (LSN), который будет использоваться в качестве нового нижнего предела для *экземпляра отслеживания*. *low_water_mark* является **двоичным (10)** и не имеет значения по умолчанию.  
  
 Если значение не равно null, оно должно быть start_lsn значением текущей записи в таблице [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) . Если в таблице cdc.lsn_time_mapping есть несколько записей, соответствующих одному моменту времени, на который ссылается указатель новой нижней конечной точки, то данному указателю присваивается наименьшее значение номера LSN данной группы записей.  
  
 Если значение явно задано как NULL, то текущая *Нижняя* граница для *экземпляра отслеживания* используется для определения верхней границы операции очистки.  
  
 [ @threshold =] "*Удаление порогового значения*"  
 Максимальное число записей, подлежащих удалению, которые могут быть удалены с помощью одной инструкции при очистке. *delete_threshold* имеет тип **bigint**и значение по умолчанию 5000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Процедура sys.sp_cdc_cleanup_change_table производит следующие операции.  
  
1.  Если @low_water_mark параметр не РАВЕН null, он задает для *экземпляра системы отслеживания* значение start_lsn, равное новому *нижнему пределу*.  
  
    > [!NOTE]  
    >  Новая нижняя конечная точка может не являться точкой, указанной в вызове хранимой процедуры. Если в таблице cdc.lsn_time_mapping есть несколько записей, соответствующих одному моменту времени, то в качестве нижней конечной точки выбирается наименьшее значение start_lsn в группе записей. Если @low_water_mark параметр имеет значение null или текущий нижний предел больше, чем новый ловватермарк, то значение start_lsn для экземпляра отслеживания остается неизменным.  
  
2.  Записи таблицы изменений, значения __$start_lsn которых меньше нижней конечной точки, удаляются. Пороговое значение удаления используется для ограничения количества строк, удаляемых в одной транзакции. Неуспешное удаление записей сопровождается выводом сообщения, но не влияет на изменения нижней конечной точки экземпляра системы отслеживания, которая могла быть создана при вызове.  

 Пользуйтесь процедурой sys.sp_cdc_cleanup_change_table в следующих случаях.  
  
-   Задание агента очистки сообщает о неудачном удалении.  
  
     Администратор может запустить данную хранимую процедуру явным образом, чтобы повторно выполнить эту операцию. Чтобы повторить очистку для данного экземпляра отслеживания, выполните хранимую процедуру sys. sp_cdc_cleanup_change_table и укажите для параметра значение NULL @low_water_mark .  
  
-   Простая политика на основе срока хранения, используемая заданием агента очистки, не является оптимальной.  
  
     Поскольку эта хранимая процедура выполняет очистку для одного экземпляра системы отслеживания, то она может быть использована для построения пользовательской стратегии очистки, которая применяет правила очистки к индивидуальному экземпляру системы отслеживания.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [CDC. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys. fn_cdc_get_min_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys. fn_cdc_increment_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)  
  
  
