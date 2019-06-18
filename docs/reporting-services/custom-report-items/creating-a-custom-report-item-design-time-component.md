---
title: Создание компонента времени разработки для пользовательского элемента отчета | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a9789c2d017200650bcae7b5f864da708e5c7453
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63194293"
---
# <a name="creating-a-custom-report-item-design-time-component"></a>Создание компонента времени разработки пользовательского элемента отчета
  Компонент времени разработки пользовательского элемента отчета ― это элемент управления, который может быть использован в конструкторе отчетов среды Visual Studio. Компонент времени разработки пользовательского элемента отчета предоставляет активную область конструктора, поддерживающую операции перетаскивания, интеграцию с браузером свойств среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и возможность использования пользовательских редакторов свойств.  
  
 Благодаря компоненту времени разработки пользователь может расположить пользовательский элемент отчета в отчете в среде конструктора, задать пользовательские свойства данных в элементе отчета и сохранить элемент отчета в виде части проекта отчета.  
  
 Свойства, заданные при помощи компонента времени разработки в среде разработки, сериализуются и десериализуются средой проектирования узла и сохраняются в виде элементов в файле на языке определения отчетов (RDL). При выполнении отчета обработчиком отчетов свойства, заданные при помощи компонента времени разработки, передаются компоненту времени выполнения пользовательского элемента отчета, который подготавливает к просмотру пользовательский элемент отчета и возвращает его обратно обработчику отчетов.  
  
> [!NOTE]
>  Компонент времени разработки для пользовательского элемента отчета реализуется в виде компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. В этом документе приводится описание реализации, характерной для компонента времени разработки пользовательского элемента отчета. Дополнительные сведения о разработке компонентов с использованием платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе [Компоненты в Visual Studio](https://go.microsoft.com/fwlink/?LinkId=116576) библиотеки MSDN.  
  
 Образец полностью реализованного пользовательского элемента отчета см. на странице [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="implementing-a-design-time-component"></a>Реализация компонента времени разработки  
 Основной класс компонента времени разработки для пользовательского элемента отчета наследуется от класса **Microsoft.ReportDesigner.CustomReportItemDesigner**. Помимо стандартных атрибутов, используемых для элемента управления [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], класс компонента также должен определять атрибут **CustomReportItem**. Этот атрибут должен соответствовать имени пользовательского элемента отчета, определенному в файле reportserver.config. Список атрибутов [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе «Атрибуты» документации по SDK [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 В следующем образце кода приводятся атрибуты, которые используются компонентом времени разработки пользовательского элемента отчета:  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a>Инициализация компонента  
 Определяемые пользователем свойства передаются пользовательскому элементу отчета при помощи класса <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>. Реализация класса **CustomReportItemDesigner** должна переопределять метод **InitializeNewComponent**, который создает экземпляр класса <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> компонента и присваивает ему значения по умолчанию.  
  
 В следующем образце кода показан класс компонента времени разработки для пользовательского элемента отчета, переопределяющий метод **CustomReportItemDesigner.InitializeNewComponent**, который инициализирует класс <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> компонента:  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a>Изменение свойств компонента  
 Свойства **CustomData** в среде разработки можно изменить несколькими способами. Любые свойства, предоставляемые компонентом времени разработки и отмеченные атрибутом <xref:System.ComponentModel.BrowsableAttribute>, можно изменить с помощью браузера свойств среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Кроме того, свойства можно изменить, перетащив элементы в область конструктора пользовательского элемента отчета или щелкнув правой кнопкой мыши элемент управления в среде разработки и выбрав в контекстном меню пункт **Свойства** для отображения окна с пользовательскими свойствами.  
  
 В следующем примере кода показано свойство **Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData** с примененным атрибутом <xref:System.ComponentModel.BrowsableAttribute>:  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 Компонент времени разработки можно снабдить диалоговым окном для редактирования пользовательских свойств. Реализация редактора пользовательских свойств должна наследовать класс <xref:System.ComponentModel.ComponentEditor> и создать экземпляр диалогового окна, который можно использовать для изменения свойств.  
  
 В следующем образце кода показана реализация класса, наследующего <xref:System.ComponentModel.ComponentEditor> и отображающего диалоговое окно редактора пользовательских свойств:  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 Диалоговое окно редактора пользовательских свойств может вызывать редактор выражений конструктора отчетов. В следующем примере редактор выражений вызывается при выборе пользователем первого элемента в поле со списком:  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a>Использование команд конструктора  
 Команда конструктора ― это команда меню, связанная с обработчиком событий. Команды конструктора можно добавить в контекстное меню компонента во время использования элемента управления времени выполнения пользовательского элемента отчета в среде конструктора. Список доступных команд конструктора возвращается из компонента времени выполнения с помощью свойства **Verbs**.  
  
 В следующем образце кода приводится команда конструктора с добавлением обработчика событий в коллекцию <xref:System.ComponentModel.Design.DesignerVerbCollection>, а также код самого обработчика событий:  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a>Использование крайних элементов  
 Классы пользовательского элемента отчета также могут реализовывать класс **Microsoft.ReportDesigner.Design.Adornment**. Крайний элемент позволяет элементу управления пользовательского элемента отчета иметь области за пределами основного прямоугольника области конструктора. Эти области могут обрабатывать события пользовательского интерфейса, такие как щелчки кнопкой мыши и операции перетаскивания. Класс **Adornment**, определенный в пространстве имен **Microsoft.ReportDesigner** служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], является транзитной реализацией класса <xref:System.Windows.Forms.Design.Behavior.Adorner>, используемого в Windows Forms. Полные сведения о классе **Adorner** см. в разделе [Общие сведения о службе расширения функциональности](https://go.microsoft.com/fwlink/?LinkId=116673) библиотеки MSDN. Образец кода, реализующего класс **Microsoft.ReportDesigner.Design.Adornment**, см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
 Дополнительные сведения о программировании и использовании форм Windows Forms в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] см. в следующих разделах библиотеки MSDN:  
  
-   Атрибуты времени разработки для компонентов  
  
-   Компоненты в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  
  
-   Пошаговое руководство. Создание элемента управления Windows Forms, использующего функции времени разработки среды Visual Studio  
  
## <a name="see-also"></a>См. также:  
 [Архитектура пользовательских элементов отчета](../../reporting-services/custom-report-items/custom-report-item-architecture.md)   
 [Создание компонента времени выполнения пользовательского элемента отчета](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Библиотеки классов пользовательских элементов отчета](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)   
 [Развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
