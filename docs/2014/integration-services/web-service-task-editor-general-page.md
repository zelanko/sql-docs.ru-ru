---
title: Редактор задачи «веб-служба» (страница «Общие») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6f993f1f2386782bf8225f22b285b9385e2f8e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054542"
---
# <a name="web-service-task-editor-general-page"></a>Редактор задачи «Веб-служба» (страница «Общие»)
  Страница **Общие** в диалоговом окне **Редактор задачи "Веб-служба"** применяется для указания диспетчера HTTP-соединений, расположения файла WSDL, используемого задачей веб-службы, описания задачи веб-службы и загрузки файла WSDL.  
  
 Дополнительные сведения об этой задаче см. в разделе [Задача "Веб-служба"](control-flow/web-service-task.md).  
  
## <a name="options"></a>Параметры  
 **HTTPConnection**  
 Выберите Диспетчер соединений из списка или нажмите кнопку \< **создать соединение...**>, чтобы создать новый диспетчер соединений.  
  
> [!IMPORTANT]  
>  Диспетчер HTTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
 **См. также: **  [Диспетчер HTTP-соединений](connection-manager/http-connection-manager.md), [Редактор диспетчера HTTP-соединений](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Введите полный путь к WSDL-файлу, который является локальным для компьютера, или нажмите кнопку обзора **(...)** и найдите этот файл.  
  
 Если WSDL-файл был загружен на компьютер вручную, выберите этот файл. Однако, если WSDL-файл еще не был загружен, выполните следующие действия.  
  
-   Создайте пустой файл с расширением WSDL.  
  
-   Выберите этот пустой файл для параметра **WSDLFile** .  
  
-   Присвойте параметру **свойство overwritewsdlfile** значение `True` , чтобы разрешить перезапись пустого файла с фактическим WSDL-файлом.  
  
-   Нажмите кнопку **Загрузить язык WSDL** , чтобы загрузить фактический WSDL-файл и перезаписать пустой файл.  
  
    > [!NOTE]  
    >  Кнопка **Загрузить язык WSDL** недоступна, пока не указано имя существующего локального файла в поле **WSDLFile** .  
  
 **OverwriteWSDLFile**  
 Укажите, можно ли перезаписать WSDL-файл для задачи веб-службы.  
  
 Если вы собираетесь загрузить WSDL-файл с помощью кнопки **скачать WSDL** , задайте для `True`этого параметра значение.  
  
 **Имя**  
 Введите уникальное имя задачи веб-службы. Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание задачи веб-службы.  
  
 **Загрузить язык WSDL**  
 Загрузите файл WSDL.  
  
 Эта кнопка недоступна, пока не указано имя существующего локального файла в поле **WSDLFile** .  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "веб-служба" &#40;"входная страница"&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Редактор задачи "веб-служба" &#40;страница "выходные данные"&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
