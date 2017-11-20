---
title: "Выполнение операции (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 01/11/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 75dc26699071ee88bb0c05368b4bf36ba677c35b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a>Выполнение операции (мастер импорта и экспорта SQL Server)
После того как вы проверите значения, выбранные в мастере, и нажмете кнопку **Готова** на странице **Завершение работы мастера** , в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется страница **Выполнение операции**. На этой странице отображается ход выполнения и результат операции, настроенной на предыдущих страницах. На этой странице никакие действия не требуются.

## <a name="screen-shot---operation-in-progress"></a>Снимок экрана: выполнение операции 
 На следующем снимке экрана показана страница **Выполнение операции** мастера в процессе выполнения операции.  
  
 ![Выполнение операции страница мастера импорта и экспорта](../../integration-services/import-export-data/media/performing-operation1.png "выполнение операции страница мастера импорта и экспорта")  

## <a name="screen-shot---operation-completed"></a>Снимок экрана: операция завершена 
 На следующем снимке экрана показана страница **Выполнение операции** мастера после завершения операции. Щелкните элемент в столбце **Сообщение** , чтобы получить дополнительные сведения о соответствующем этапе.  
  
 ![Выполнение операции страница мастера импорта и экспорта](../../integration-services/import-export-data/media/performing-operation2.png "выполнение операции страница мастера импорта и экспорта")  
  
## <a name="watch-the-progress-of-the-operation"></a>Просмотр хода выполнения операции
 **Действие**  
 Отображает каждый этап операции.  
  
 **Состояние**  
 Отображает успешное или сбойное выполнение каждого этапа.  
  
 **Сообщение**  
 Отображает связанные с соответствующим этапом уведомления и сообщения об ошибках. Щелкните элемент в этом столбце, чтобы получить дополнительные сведения о соответствующем этапе.

## <a name="interrupt-the-operation-or-save-the-results"></a>Прерывание операции или сохранение результатов
 **Остановить**  
 Кнопка **Остановить** позволяет прервать операцию в случае необходимости.  
  
 **Отчет**  
 Позволяет просмотреть отчет о результатах, сохранить его в файл, скопировать его в буфер обмена или отправить по электронной почте.  
  
## <a name="whats-next"></a>Дальнейшие действия  
 После успешного выполнения настроенной операции работа с мастером импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет закончена.  
-   Если операция запускается сразу, вы можете открыть выбранное место назначения и просмотреть скопированные мастером данные.  
-   Если вы сохранили созданный мастером пакет SSIS, его можно открыть в SQL Server Data Tools для настройки и повторного использования. Сведения о настройке сохраненного пакета и его последующем запуске см. в разделе [Сохранение пакета служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).

## <a name="see-also"></a>См. также:
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



