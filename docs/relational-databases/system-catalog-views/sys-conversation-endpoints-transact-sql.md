---
title: sys.conversation_endpoints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- conversation_endpoints_TSQL
- conversation_endpoints
- sys.conversation_endpoints
- sys.conversation_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.conversation_endpoints catalog view
ms.assetid: 2ed758bc-2a9d-4831-8da2-4b80e218f3ea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 16d29272e4229ac93b3dd5b1eaf5502a07fb0a2a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109544"
---
# <a name="sysconversationendpoints-transact-sql"></a>sys.conversation_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Каждая сторона диалога компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] представляется конечной точкой диалога. Это представление каталога содержит одну запись на каждую конечную точку диалога в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|conversation_handle|**uniqueidentifier**|Идентификатор данной конечной точки диалога. Не допускает значения NULL.|  
|conversation_id|**uniqueidentifier**|Идентификатор диалога. , совместно используемый обеими сторонами диалога. В паре с содержимым столбца is_initiator уникален в рамках одной этой базы данных. Не допускает значения NULL.|  
|is_initiator|**tinyint**|Является ли данная конечная точка инициатором или целевой точкой диалога.  Не допускает значения NULL.<br /><br /> 1 = инициатор;<br /><br /> 0 = целевая точка.|  
|service_contract_id|**int**|Идентификатор контракта для диалога. Не допускает значения NULL.|  
|conversation_group_id|**uniqueidentifier**|Идентификатор группы сообщений, которой принадлежит данный диалог. Не допускает значения NULL.|  
|service_id|**int**|Идентификатор службы для этой стороны диалога. Не допускает значения NULL.|  
|lifetime|**datetime**|Дата и время окончания диалога. Не допускает значения NULL.|  
|state|**char(2)**|Текущее состояние диалога. Не допускает значения NULL. Может принимать одно из следующих значений.<br /><br /> Поэтому запущен на отправку. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обработал инструкцию BEGIN CONVERSATION для этого диалога, но пока не отправлено ни одного сообщения.<br /><br /> SI начат прием данных. Другой экземпляр запущен в новом диалоге с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] еще не до конца получил первое сообщение. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может создать диалог в этом состоянии в том случае, если первая передача фрагментирована или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получает передачу вне порядка. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может создать диалог сразу в состоянии CO (ведение диалога), если первая передача, полученная для диалога, содержит первое сообщение целиком.<br /><br /> CO обменивающиеся данными. Диалог открыт, и обе стороны диалога могут отправлять сообщения. Для большинства служб большая часть обмена данными происходит, когда диалог находится в этом состоянии.<br /><br /> DI Disconnected входящего трафика. Удаленной стороной диалога была выполнена инструкция END CONVERSATION. Состояние диалога остается неизменным до тех пор, пока локальная сторона диалога не выдаст сообщение END CONVERSATION. Приложение может продолжать получать сообщения для диалога. Поскольку удаленная сторона диалога закончила диалог, приложение не может отправлять сообщения в этом диалоге. Когда приложение выполняет инструкцию END CONVERSATION, диалог переходит в состояние CD (закрыто).<br /><br /> DO отключена отправка. Локальной стороной диалога была выполнена инструкция END CONVERSATION. Состояние диалога остается неизменным до тех пор, пока удаленная часть диалога не подтвердит сообщение END CONVERSATION. Приложение не может отправлять и получать сообщения для диалога. Когда удаленная сторона диалога подтверждает сообщение END CONVERSATION, диалог переходит в состояние CD (закрыто).<br /><br /> Ошибка аварийного восстановления. В данной конечной точке произошла ошибка. Сообщение об ошибке помещено в очередь приложений. Если очередь приложений пуста, значит это сообщение об ошибке уже обработано приложением.<br /><br /> Закрыто компакт-диска. Конечная точка диалога больше не используется.|  
|state_desc|**nvarchar(60)**|Описание состояния конечной точки диалога. Этот столбец допускает значение NULL. Может принимать одно из следующих значений.<br /><br /> **STARTED_OUTBOUND**<br /><br /> **STARTED_INBOUND**<br /><br /> **ДИАЛОГ**<br /><br /> **DISCONNECTED_INBOUND**<br /><br /> **DISCONNECTED_OUTBOUND**<br /><br /> **ЗАКРЫТО**<br /><br /> **ERROR**|  
|far_service|**nvarchar(256)**|Название службы на удаленной стороне диалога. Не допускает значения NULL.|  
|far_broker_instance|**nvarchar(128)**|Экземпляр брокера на удаленной стороне диалога. Допускает значение NULL.|  
|principal_id|**int**|Идентификатор участника, чей сертификат используется на локальной стороне диалога. Не допускает значения NULL.|  
|far_principal_id|**int**|Идентификатор пользователя, чей сертификат используется удаленной стороной диалога. Не допускает значения NULL.|  
|outbound_session_key_identifier|**uniqueidentifier**|Идентификатор исходящего ключа шифрования данного диалога. Не допускает значения NULL.|  
|inbound_session_key_identifier|**uniqueidentifier**|Идентификатор входящего ключа шифрования данного диалога. Не допускает значения NULL.|  
|security_timestamp|**datetime**|Время создания локального сеансового ключа сеанса. Не допускает значения NULL.|  
|dialog_timer|**datetime**|Время, когда таймер диалога отправляет сообщение DialogTimer. Не допускает значения NULL.|  
|send_sequence|**bigint**|Номер следующего сообщения в последовательности отправки. Не допускает значения NULL.|  
|last_send_tran_id|**binary(6)**|Внутренний идентификатор транзакции для отправки сообщения. Не допускает значения NULL.|  
|end_dialog_sequence|**bigint**|Порядковый номер сообщения End Dialog. Не допускает значения NULL.|  
|receive_sequence|**bigint**|Номер следующего сообщения, ожидаемого в последовательности приема. Не допускает значения NULL.|  
|receive_sequence_frag|**int**|Номер следующего фрагмента сообщения, ожидаемого в последовательности приема. Не допускает значения NULL.|  
|system_sequence|**bigint**|Порядковый номер сообщения последнего системного сообщения для этого диалога. Не допускает значения NULL.|  
|first_out_of_order_sequence|**bigint**|Порядковый номер первого ошибочного сообщения для этого диалога. Не допускает значения NULL.|  
|last_out_of_order_sequence|**bigint**|Порядковый номер последнего ошибочного сообщения для этого диалога. Не допускает значения NULL.|  
|last_out_of_order_frag|**int**|Порядковый номер последнего ошибочного фрагмента сообщения для этого диалога. Не допускает значения NULL.|  
|is_system|**bit**|1, если это системный диалог. Не допускает значения NULL.|  
|priority|**tinyint**|Приоритет диалога, назначенный для этой конечной точки диалога. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
