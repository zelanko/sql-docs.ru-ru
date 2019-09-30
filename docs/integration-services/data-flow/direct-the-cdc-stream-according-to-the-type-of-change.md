---
title: Выбор направления потока CDC в соответствии с типом изменения | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7af6ce4ebf3e412c2283e16e008cfd97cd34df0a
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71292834"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a>Выбор направления потока CDC в соответствии с типом изменения

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Чтобы можно было добавить и настроить преобразование «Разделитель CDC», пакет должен содержать по крайней мере одну задачу «Поток данных» и источник CDC.  
  
 Для источника CDC, добавленного к пакету, должен быть выбран режим обработки NetCDC. Дополнительные сведения о выборе режимов обработки см. в разделе [Редактор источника "CDC" (страница "Диспетчер соединений")](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md).  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a>Выбор направления потока CDC в соответствии с типом изменения  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]откройте проект служб [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , содержащий необходимый пакет.  
  
2.  В Обозревателе решений дважды щелкните пакет, чтобы его открыть.  
  
3.  Щелкните вкладку **Поток данных** , а затем **Панель инструментов**перетащите разделитель CDC в область конструктора.  
  
4.  Установите соединение источника CDC, который включен в пакет, с разделителем CDC.  
  
5.  Установите соединение разделителя CDC с одним или несколькими назначениями. Предусмотрена возможность подключить до трех различных выводов.  
  
6.  Выберите один из следующих выводов.  
  
    -   Вывод удаления. Вывод, в который направляются строки изменения DELETE.  
  
    -   Вывод вставки. Вывод, в который направляются строки изменения INSERT.  
  
    -   Вывод обновления. Вывод, в который направляются строки перед и после изменения UPDATE и строки изменения Merge.  
  
7.  Кроме того, можно настроить дополнительные свойства, используя диалоговое окно **Расширенный редактор** .  
  
     Диалоговое окно **Расширенный редактор** содержит свойства, которые могут быть заданы программным путем.  
  
     Открытие диалогового окна **Расширенный редактор** .  
  
    -   На экране **Поток данных** вашего проекта [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] щелкните правой кнопкой мыши разделитель CDC и выберите элемент **Показать расширенный редактор**.  
  
     Дополнительные сведения об использовании разделителя CDC см. в разделе «Компоненты CDC для служб Microsoft SQL Server Integration Services».  
  
## <a name="see-also"></a>См. также:  
 [Разделитель CDC](../../integration-services/data-flow/cdc-splitter.md)  
  
  
