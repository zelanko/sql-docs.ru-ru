---
title: "Редактор задачи &#171;Веб-служба&#187; (страница &#171;Общие&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.webservicestask.general.f1"
helpviewer_keywords: 
  - "редактор задачи «Веб-служба»"
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# Редактор задачи &#171;Веб-служба&#187; (страница &#171;Общие&#187;)
  Страница **Общие** в диалоговом окне **Редактор задачи "Веб-служба"** применяется для указания диспетчера HTTP-соединений, расположения файла WSDL, используемого задачей веб-службы, описания задачи веб-службы и загрузки файла WSDL.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](../../integration-services/control-flow/web-service-task.md).  
  
## Параметры  
 **HTTPConnection**  
 Выберите диспетчер соединений из списка или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
> [!IMPORTANT]  
>  Диспетчер HTTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
 **См. также**: [Диспетчер HTTP-соединений](../../integration-services/connection-manager/http-connection-manager.md), [Редактор диспетчера HTTP-соединений](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Введите полный путь к локальному WSDL-файлу на компьютере или нажмите кнопку обзора **(…)** и выберите файл.  
  
 Если WSDL-файл был загружен на компьютер вручную, выберите этот файл. Однако, если WSDL-файл еще не был загружен, выполните следующие действия.  
  
-   Создайте пустой файл с расширением WSDL.  
  
-   Выберите этот пустой файл для параметра **WSDLFile** .  
  
-   Установите свойство **OverwriteWSDLFile** в значение **True** , чтобы разрешить перезапись пустого файла фактическим WSDL-файлом.  
  
-   Нажмите кнопку **Загрузить язык WSDL** , чтобы загрузить фактический WSDL-файл и перезаписать пустой файл.  
  
    > [!NOTE]  
    >  Кнопка **Загрузить язык WSDL** недоступна, пока не указано имя существующего локального файла в поле **WSDLFile**.  
  
 **OverwriteWSDLFile**  
 Укажите, можно ли перезаписать WSDL-файл для задачи веб-службы.  
  
 Если нужно загрузить WSDL-файл с помощью кнопки **Загрузить язык WSDL** , установите это свойство в значение **True**.  
  
 **Название**  
 Введите уникальное имя задачи веб-службы. Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Description**  
 Введите описание задачи веб-службы.  
  
 **Download WSDL**  
 Загрузите файл WSDL.  
  
 Эта кнопка недоступна, пока не указано имя существующего локального файла в поле **WSDLFile** .  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Веб-служба" (страница "Ввод")](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [Редактор задачи "Веб-служба" (страница "Вывод")](../../integration-services/control-flow/web-service-task-editor-output-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
  