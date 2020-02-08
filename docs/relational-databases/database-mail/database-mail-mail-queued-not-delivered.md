---
title: 'Компонент Database Mail: Письмо в очереди не доставлено | Документация Майкрософт'
ms.custom: ''
ms.date: 04/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92ff867d98b83f1934972a576df8295c3f9ca79d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "70228409"
---
# <a name="database-mail-mail-queued-not-delivered"></a>Компонент Database Mail: Письмо в очереди не доставлено 
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

В этом подразделе описывается, как решать проблему, когда электронное сообщение успешно ставится в очередь, но не доставляется.

## <a name="diagnose-the-problem"></a>Диагностика проблемы 

Внешняя программа компонента Database Mail ведет журнал активности электронной почты в базе данных **msdb**.

Чтобы убедиться, что компонент Database Mail включен, воспользуйтесь параметром [Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) системной хранимой процедуры **sp_configure**, как в следующем примере.

```sql 
EXEC sp_configure 'show advanced', 1;  
RECONFIGURE; 
EXEC sp_configure; 
GO
```

Затем, чтобы проверить состояние почтовой очереди, выполните следующую инструкцию в базе данных **msdb**:

```sql
sysmail_help_queue_sp @queue_type = 'Mail' ;
```

Подробное описание столбцов см. в разделе [sysmail_help_queue_sp (Transact-SQL)](../system-stored-procedures/sysmail-help-queue-sp-transact-sql.md#result-set).

Проверьте, есть ли какие-либо изменения представления **sysmail_event_log**. В этом представлении должна находиться запись, удостоверяющая, что запущена внешняя программа компонента Database Mail. Если ее нет в представлении **sysmail_event_log**, см. раздел [Сообщение поставлено в очередь, но записей нет](database-mail-common-errors.md#database-mail-queued-no-entries-in-sysmail_event_log-or-windows-application-event-log) в **sysmail_event_log**. Если в представлении **sysmail_event_log** появились ошибки, устраните их.

Если в представлении **sysmail_event_log** есть записи, свидетельствующие о запуске внешней программы, проверьте сообщения о состоянии в представлении **sysmail_allitems**.

## <a name="message-status-unsent"></a>Состояние сообщения — не отправлено 

Состояние **не отправлено** означает, что [внешняя программа компонента Database Mail](database-mail-external-program.md) еще не обработала электронное сообщение. Иногда она не очень быстро это делает, скорость их обработки зависит от параметров сети, времени ожидания перед повтором, объема сообщений и ресурсов SMTP-сервера. Если проблема остается, попробуйте отсылать сообщения из нескольких профилей и с нескольких SMTP-серверов.

Проверьте последнюю дату успешной отправки сообщений. Если после последней успешной отправки прошло много времени, через представление sysmail_event_log убедитесь, что внешняя программа была успешно запущена компонентом Service Broker. Если последняя попытка активировать программу завершилась ошибкой, убедитесь, что внешняя программа компонента Database Mail находится в верном каталоге и учетная запись службы SQL Server имеет разрешения на ее запуск.

   > [!NOTE]
   > Чтобы удалить старые неотправленные сообщения, дождитесь момента, когда они станут самыми старыми сообщениями в очереди, а затем воспользуйтесь хранимой процедурой [sysmail_delete_mailitems_sp](../system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md) для их удаления.

## <a name="message-status-retrying"></a>Состояние сообщения — идет повтор

Состояние «retrying» свидетельствует о том, что компонент Database Mail попытался доставить сообщение, но SMTP-сервер не смог этого сделать. Обычно причиной служат ошибки в сети, сбой SMTP-сервера или неправильная конфигурация учетной записи компонента Database Mail. Рано или поздно это сообщение будет отправлено или не отправлено и сохранено в состоянии ошибки и с записью в журнале событий.

## <a name="message-status-sent"></a>Состояние сообщения — отправлено

Состояние **отправлено** означает, что внешняя программа компонента Database Mail успешно доставила электронное сообщение SMTP-серверу. Если у получателя сообщение не появилось, то это означает, что SMTP-сервер принял сообщение от компонента Database Mail, но не смог доставить его получателю. Проверьте журналы SMTP-сервера или свяжитесь с его администратором. SMTP-сервер также можно проверить с помощью другого почтового клиента, например Outlook Express.

## <a name="message-status-failed"></a>Состояние сообщения — сбой

Состояние "Сбой" означает, что внешняя программа компонента Database Mail не смогла доставить электронное сообщение SMTP-серверу. В этом случае в представлении **sysmail_event_log** есть подробные сведения, полученные из внешней программы. Образец запроса, соединяющего представления **sysmail_faileditems** и **sysmail_event_log** для получения сообщений об ошибках, см. в разделе [Проверка состояния сообщений электронной почты, отправленных при помощи компонента Database Mail](check-the-status-of-e-mail-messages-sent-with-database-mail.md). Наиболее частая причина ошибок — неверный адрес получателя, проблемы в сети, из-за которых внешняя программа не может использовать учетные записи отработки отказа. Проблемы SMTP-сервера также могут быть причиной того, что сообщения сервером отклоняются. Чтобы выяснить, где происходит ошибка, в мастере настройки компонента Database Mail измените значение параметра **Уровень ведения журнала** на **Подробный** и отправьте тестовое сообщение.



##  <a name="RelatedContent"></a> См. также
  
-  [Общие сведения о компоненте Database Mail](database-mail.md)

  
  
