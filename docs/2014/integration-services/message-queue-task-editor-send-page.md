---
title: Редактор задачи «очередь сообщений» (страница «отправка») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.send.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c78b6665e761b0ffa9da4a4abcefc2489bff07a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424691"
---
# <a name="message-queue-task-editor-send-page"></a>Редактор задачи «Очередь сообщений» (страница «Отправка»)
  Используйте страницу **Отправить** диалогового окна **Редактор задачи "Очередь сообщений"**, чтобы настроить задачу "Очередь сообщений" для отправки сообщений от пакета служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Дополнительные сведения об этой задаче см. в разделе [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Параметры  
 **UseEncryption**  
 Укажите, необходимо ли шифровать сообщение. Значение по умолчанию — `False`.  
  
 **EncryptionAlgorithm**  
 При выборе шифрования задайте имя алгоритма шифрования для использования. Задача «Очередь сообщений» поддерживает алгоритмы RC2 и RC4. По умолчанию, используется алгоритм **RC2**.  
  
> [!NOTE]  
>  Алгоритм RC4 поддерживается только в целях обратной совместимости. Когда база данных имеет уровень совместимости 90 или 100, новые материалы могут шифроваться только с помощью алгоритмов RC4 или RC4_128. (Не рекомендуется.) Используйте вместо этого более новые алгоритмы, например AES. В текущем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] материалы, зашифрованные с помощью алгоритмов RC4 или RC4_128, могут быть расшифрованы на любом уровне совместимости.  
  
> [!IMPORTANT]  
>  Здесь приведены алгоритмы шифрования, поддерживаемые технологией очередей сообщений (MSMQ). Оба этих алгоритма шифрования считаются сегодня криптографически слабыми по сравнению с новыми алгоритмами, которые служба очередей сообщений еще не поддерживает. Поэтому при отправке сообщений с помощью задачи «Очередь сообщений» необходимо тщательно учитывать требования криптографии.  
  
 **MessageType**  
 Выбор типа сообщения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|**Сообщение файла данных**|Сообщение хранится в файле. При выборе этого значения отображается динамический параметр **DataFileMessage**.|  
|**Сообщение переменной**|Сообщение хранится в переменной. При выборе этого значения отображается динамический параметр **VariableMessage**.|  
|**Строковое сообщение**|Сообщение сохраняется в задаче «Очередь сообщений». При выборе этого значения отображается динамический параметр **StringMessage**.|  
  
## <a name="messagetype-dynamic-options"></a>Динамические параметры MessageType  
  
### <a name="messagetype--data-file-message"></a>MessageType = Сообщение файла данных  
 **DataFileMessage**  
 Введите путь к файлу данных или нажмите кнопку с многоточием **(...)** и найдите файл.  
  
### <a name="messagetype--variable-message"></a>MessageType = Сообщение с переменными  
 **VariableMessage**  
 Введите имена переменных или нажмите кнопку с многоточием **(...)** , а затем выберите переменные. Переменные разделяются запятыми.  
  
 **См. также:** Выбор переменных  
  
### <a name="messagetype--string-message"></a>MessageType = Строковое сообщение  
 **StringMessage**  
 Введите строковое сообщение или нажмите кнопку с многоточием **(...)** , а затем введите сообщение в диалоговом окне **Введите строковое сообщение** .  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "очередь сообщений" &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "очередь сообщений" &#40;"получить страницу"&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
