---
title: "Создание компонента пользовательского элемента отчета времени разработки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
caps.latest.revision: 37
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2cb994a0cb4dde6b6ea5f671238272e574e7721b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="creating-a-custom-report-item-design-time-component"></a>Создание компонента времени разработки пользовательского элемента отчета
  Компонент времени разработки пользовательского элемента отчета ― это элемент управления, который может быть использован в конструкторе отчетов среды Visual Studio. Компонент времени разработки пользовательского элемента отчета предоставляет активную область конструктора, поддерживающую операции перетаскивания, интеграцию с браузером свойств среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и возможность использования пользовательских редакторов свойств.  
  
 Благодаря компоненту времени разработки пользователь может расположить пользовательский элемент отчета в отчете в среде конструктора, задать пользовательские свойства данных в элементе отчета и сохранить элемент отчета в виде части проекта отчета.  
  
 Свойства, заданные при помощи компонента времени разработки в среде разработки, сериализуются и десериализуются средой проектирования узла и сохраняются в виде элементов в файле на языке определения отчетов (RDL). При выполнении отчета обработчиком отчетов свойства, заданные при помощи компонента времени разработки, передаются компоненту времени выполнения пользовательского элемента отчета, который подготавливает к просмотру пользовательский элемент отчета и возвращает его обратно обработчику отчетов.  
  
> [!NOTE]  
>  Реализован в виде компонента пользовательского элемента отчета времени разработки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] компонента. В этом документе приводится описание реализации, характерной для компонента времени разработки пользовательского элемента отчета. Дополнительные сведения о разработке компонентов с использованием [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], в разделе [компоненты в Visual Studio](http://go.microsoft.com/fwlink/?LinkId=116576) в библиотеке MSDN.  
  
 Образец полностью реализованного пользовательского элемента отчета см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="implementing-a-design-time-component"></a>Реализация компонента времени разработки  
 Основной класс компонента пользовательского элемента отчета времени разработки наследуется от **Microsoft.ReportDesigner.CustomReportItemDesigner** класса. Помимо стандартных атрибутов, используемых для [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] управления, необходимо определить класс компонента **CustomReportItem** атрибута. Этот атрибут должен соответствовать имени пользовательского элемента отчета, определенному в файле reportserver.config. Список атрибутов [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе «Атрибуты» документации по SDK [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
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
 Определяемые пользователем свойства передаются пользовательскому элементу отчета при помощи класса <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>. Реализация **CustomReportItemDesigner** класс должен переопределять **InitializeNewComponent** метод для создания нового экземпляра компонента <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> класса и присвойте ему значение значения по умолчанию.  
  
 В следующем примере кода показан пример пользовательского отчета элемента компонента времени разработки класс переопределения **CustomReportItemDesigner.InitializeNewComponent** метод для инициализации компонента <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> класса:  
  
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
 Вы можете изменить **CustomData** свойства в среде разработки несколькими способами. Любые свойства, предоставляемые компонентом времени разработки и отмеченные атрибутом <xref:System.ComponentModel.BrowsableAttribute>, можно изменить с помощью браузера свойств среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Кроме того, можно изменить свойства путем перетаскивания элементов в область конструирования пользовательского элемента отчета, или щелкните правой кнопкой мыши элемент управления в среде разработки и выбрав **свойства** контекстного меню для отображения окна с пользовательскими свойствами.  
  
 В следующем примере кода показан **Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData** свойство, имеющее <xref:System.ComponentModel.BrowsableAttribute> применен атрибут:  
  
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
 Команда конструктора ― это команда меню, связанная с обработчиком событий. Команды конструктора можно добавить в контекстное меню компонента во время использования элемента управления времени выполнения пользовательского элемента отчета в среде конструктора. Может возвращать список доступных команд конструктора из компонента времени выполнения с помощью **команд** свойство.  
  
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
 Также можно реализовать классы пользовательского элемента отчета **Microsoft.ReportDesigner.Design.Adornment** класса. Крайний элемент позволяет элементу управления пользовательского элемента отчета иметь области за пределами основного прямоугольника области конструктора. Эти области могут обрабатывать события пользовательского интерфейса, такие как щелчки кнопкой мыши и операции перетаскивания. **Оформления** класс, который определен в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **Microsoft.ReportDesigner** пространством имен является транзитной реализацией <xref:System.Windows.Forms.Design.Behavior.Adorner> найти класс в Windows Forms. Полную документацию по **графический элемент** см. в описании [Общие сведения о службе поведения](http://go.microsoft.com/fwlink/?LinkId=116673) в библиотеке MSDN. Пример кода, который реализует **Microsoft.ReportDesigner.Design.Adornment** см. в описании [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
 Дополнительные сведения о программировании и использовании форм Windows Forms в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] см. в следующих разделах библиотеки MSDN:  
  
-   Атрибуты времени разработки для компонентов  
  
-   Компоненты в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  
  
-   Пошаговое руководство: Создание элемента управления Windows Forms, используются преимущества функций Visual Studio во время разработки  
  
## <a name="see-also"></a>См. также:  
 [Архитектура пользовательского элемента отчета](../../reporting-services/custom-report-items/custom-report-item-architecture.md)   
 [Создание компонента пользовательского элемента отчета времени выполнения](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Библиотеки классов элемента пользовательского отчета](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)   
 [Как: развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
