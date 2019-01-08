---
title: Редактор назначения SAP BW (страница "Вывод ошибок") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 68154507fe6985a831c54c4c497d1d4c8300851d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764056"
---
# <a name="sap-bw-destination-editor-error-output-page"></a>Редактор назначений SAP BW (страница «Вывод ошибок»)
  Используйте страницу **Вывод ошибок** диалогового окна **Редактор назначений SAP BW** для задания параметров обработки ошибок.  
  
 Для получения дополнительных сведений о назначении SAP BW для [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 для SAP BW см. раздел [Назначение SAP BW](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие страницы «Вывод ошибок»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В окне **Редактор назначений SAP BW**щелкните **Вывод ошибок** , чтобы открыть страницу редактора **Вывод ошибок** .  
  
## <a name="options"></a>Параметры  
  
> [!NOTE]  
>  Если вы не знаете все значения, необходимые для настройки назначения, может потребоваться связаться с администратором SAP.  
  
 **Вход или выход**  
 Просмотрите имя входных данных.  
  
 **Столбец**  
 Данный параметр не используется.  
  
 **Ошибка**  
 Задайте действие, которое необходимо выполнить в назначении при возникновении ошибки: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Усечение**  
 Данный параметр не используется.  
  
 **Описание**  
 Просмотрите описание операции.  
  
 **Присвоить указанное значение выбранным ячейкам**  
 Укажите действие, которое необходимо применить в назначении ко всем выбранным ячейкам при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Применить**  
 Применить параметр обработки ошибок к выбранным ячейкам.  
  
## <a name="see-also"></a>См. также  
 [Редактор назначений SAP BW (страница "Диспетчер подключений")](sap-bw-destination-editor-connection-manager-page.md)   
 [Редактор назначений SAP BW (страница "Сопоставления")](sap-bw-destination-editor-mappings-page.md)   
 [Редактор назначений SAP BW (страница "Дополнительно")](sap-bw-destination-editor-advanced-page.md)   
 [Справка F1 по Microsoft Connector 1.1 для SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
