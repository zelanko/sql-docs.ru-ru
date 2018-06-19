---
title: Создание или развертывание кэша для преобразования "Уточняющий запрос" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating cache files for Lookup transformation
- deploying cache files for Lookup transformation
- Lookup transformation cache files
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c1b6a884fa31a6e2ea90889c750ee5306ebc5e1c
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400796"
---
# <a name="create-and-deploy-a-cache-for-the-lookup-transformation"></a>Создание или развертывание кэша для преобразования «Уточняющий запрос»
  Можно создать и развернуть файл кэша (CAW) для преобразования «Уточняющий запрос». Эталонный набор данных хранится в файле кэша.  
  
 Преобразование «Уточняющий запрос» выполняет уточняющие запросы, соединяя данные из входных столбцов подключенного источника данных и данные из столбцов в эталонном наборе данных.  
  
 Файл кэша создается с помощью диспетчера соединений с кэшем и преобразования «Преобразование кэша». Дополнительные сведения см. в разделах [Cache Connection Manager](../../../integration-services/data-flow/transformations/cache-connection-manager.md) и [Cache Transform](../../../integration-services/data-flow/transformations/cache-transform.md).  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос» и файлах кэша см. в разделе [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
### <a name="to-create-a-cache-file"></a>Создание файла кэша  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]откройте проект [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет, и затем откройте пакет.  
  
2.  На вкладке **Поток управления** добавьте задачу потока данных.  
  
3.  На вкладке **Поток данных** добавьте преобразование «Преобразование кэша» к потоку данных, а затем подключите преобразование к источнику данных.  
  
     При необходимости настройте источник данных.  
  
4.  Дважды щелкните "Преобразование кэша", а затем в окне **Редактор преобразований кэша**на странице **Диспетчер соединений** щелкните **Создать** , чтобы создать новый диспетчер соединений с кэшем.  
  
5.  В окне **Редактор диспетчера соединений с кэшем**на вкладке **Общее** настройте конфигурацию диспетчера соединений с кэшем, чтобы сохранить кэш, выбрав следующие параметры.  
  
    1.  Выберите **Использовать кэш файлов**.  
  
    2.  В поле **Имя файла**введите путь к файлу.  
  
     Файл создается системой при выполнении пакета.  
  
    > [!NOTE]  
    >  Уровень защиты пакета не применяется к кэшируемому файлу. Если кэшируемый файл содержит важные данные, используйте список управления доступом (ACL), чтобы запретить доступ к расположению или папке, в которой хранится файл. Доступ следует разрешать только определенным учетным записям. Дополнительные сведения см. в разделе [Доступ к файлам, используемым пакетами](../../../integration-services/security/security-overview-integration-services.md#files).  
  
6.  Перейдите на вкладку **Столбцы** , а затем задайте, какие столбцы будут столбцами индекса, с помощью параметра **Позиция индекса** .  
  
     Для неиндексированных столбцов позиция индекса равна 0. Для индексированных столбцов позиция индекса является положительным порядковым номером.  
  
    > [!NOTE]  
    >  Если преобразование «Уточняющий запрос» настроено для использования диспетчера соединений с кэшем, то только индексированные столбцы в ссылочном наборе данных могут быть сопоставлены с входными столбцами. Кроме того, все столбцы индекса должны быть сопоставлены.  
  
     Дополнительные сведения см. в разделе [Cache Connection Manager Editor](../../../integration-services/data-flow/transformations/cache-connection-manager-editor.md).  
  
7.  При необходимости настройте преобразование кэша.  
  
     Дополнительные сведения см. в разделах [Редактор преобразования "Кэш" (страница "Диспетчер соединений")](../../../integration-services/data-flow/transformations/cache-transformation-editor-connection-manager-page.md) и [Редактор преобразования "Кэш" (страница "Сопоставления")](../../../integration-services/data-flow/transformations/cache-transformation-editor-mappings-page.md).  
  
8.  Запустите пакет.  
  
### <a name="to-deploy-a-cache-file"></a>Развертывание файла кэша  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]откройте проект [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет, и затем откройте пакет.  
  
2.  При необходимости создайте конфигурацию пакета. Дополнительные сведения см. в разделе [Создание конфигурации пакетов](../../../integration-services/packages/create-package-configurations.md).  
  
3.  Добавьте файл кэша к проекту, выполнив следующие действия.  
  
    1.  В обозревателе решений выберите проект, который был открыт в шаге 1.  
  
    2.  В меню **Проект** выберите пункт **Добавить существующий элемент**.  
  
    3.  Выберите файл кэша и нажмите кнопку **Добавить**.  
  
     Файл появится в папке **Разное** в обозревателе решений.  
  
4.  Настройте проект для создания программы развертывания, а затем постройте проект. Дополнительные сведения см. в статье [Create a Deployment Utility](../../../integration-services/packages/create-a-deployment-utility.md).  
  
     Создается файл манифеста \<*имя проекта*>.SSISDeploymentManifest.xml, в котором перечислены различные файлы в проекте, пакеты и конфигурации пакетов.  
  
5.  Развертывание пакета в файловой системе. Дополнительные сведения см. в статье [Deploy Packages by Using the Deployment Utility](../../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md).  
  
## <a name="see-also"></a>См. также:  
 [Create a Deployment Utility](../../../integration-services/packages/create-a-deployment-utility.md)  
  
  
