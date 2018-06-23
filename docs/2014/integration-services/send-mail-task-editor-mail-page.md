---
title: Редактор Отправка почты задачи (страница «почта») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b65b2b385489073010d853ea01c3f6feb2a1924b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100227"
---
# <a name="send-mail-task-editor-mail-page"></a>Редактор задачи «Отправка почты» (страница «Почта»)
  Страница **Почта** диалогового окна **Редактор задачи «Отправка почты»** служит для определения получателей, типа и приоритета сообщения. К сообщению можно также прикрепить файлы. Текстом сообщения может быть введенная строка, соединение с файлом, содержащим текст, или имя переменной, содержащей текст.  
  
 Дополнительные сведения об этой задаче см. в разделе [Send Mail Task](control-flow/send-mail-task.md).  
  
## <a name="options"></a>Параметры  
 **SMTPConnection**  
 Выберите диспетчер подключений SMTP из списка или щелкните **\<Создать соединение…>**, чтобы создать его.  
  
> [!IMPORTANT]  
>  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
 **См. также:** [Диспетчер соединений SMTP](connection-manager/smtp-connection-manager.md)  
  
 **От**  
 Задайте адрес электронной почты отправителя.  
  
 **Чтобы**  
 Укажите адреса электронной почты получателей, разделенные точкой с запятой.  
  
 **Копия**  
 Задайте адреса электронной почты получателей, которые также получают копии сообщения. Разделяйте адреса точками с запятой.  
  
 **Скрытая копия**  
 Задайте адреса электронной почты получателей, которые получают скрытые копии сообщения. Разделяйте адреса точками с запятой.  
  
 **Тема**  
 Укажите тему электронного сообщения.  
  
 **MessageSourceType**  
 Выберите тип источника сообщения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Прямой ввод**|Задание источника текста сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
|**Соединение с файлом**|Задание в качестве источника файла, содержащего текст сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
|**Переменная**|В качестве источника указывается переменная, содержащая текст сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
  
 **Приоритет**  
 Задается приоритет сообщения.  
  
 **Вложения**  
 Укажите имена вложений для электронного сообщения, разделенные символом вертикальной черты (|).  
  
> [!NOTE]  
>  Длина строк «Кому», «Копия» и «СК» ограничена 256 символами в соответствии со стандартами Интернета.  
  
## <a name="messagesourcetype-dynamic-options"></a>Динамические параметры MessageSourceType  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Прямой ввод  
 **MessageSource**  
 Введите текст сообщения или нажмите кнопку обзора (…), а затем введите сообщение в диалоговом окне **Источник сообщения** .  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Соединение с файлом  
 **MessageSource**  
 Выберите диспетчер подключений файлов из списка или щелкните \<**Создать соединение…**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Переменная  
 **MessageSource**  
 Выберите переменную из списка или нажмите кнопку \<**Создать переменную…**>, чтобы создать переменную.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md), [Добавление переменной](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор Отправка почты задач &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница "Выражения"](expressions/expressions-page.md)  
  
  