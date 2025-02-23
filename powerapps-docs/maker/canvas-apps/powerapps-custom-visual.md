---
title: PowerApps custom visual for Power BI | Microsoft Docs
description: Procedure and limitations for embedding a canvas app that uses the same data source and can be filtered like other report items in Power BI 
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/23/2019
ms.author: chmoncay
search.audienceType: 
  - maker
search.app: 
  - PowerApps
---

# PowerApps custom visual for Power BI

Power BI enables data insights and better decision-making, while PowerApps enables everyone to build and use apps that connect to business data. Using the PowerApps custom visual, you can pass context-aware data to a canvas app, which updates in real time as you make changes to your report. Now, your app users can derive business insights and take actions from right within their Power BI reports and dashboards.

## Using the PowerApps custom visual

Let's look at the steps required to use the PowerApps custom visual in your Power BI report.

1. Get the custom visual from [AppSource](https://appsource.microsoft.com/product/power-bi-visuals/WA104381378?tab=Overview) or directly import it in the Power BI service.

    ![Custom visual in marketplace](./media/powerapps-custom-visual/powerapps-store.png) 

2. Add the PowerApps visual to your report, and set the data fields associated with it.

    ![Select report data](./media/powerapps-custom-visual/add-visual-set-data.png)

    You can choose an existing app or create one, but the report must be published to the Power BI service and opened in Microsoft Edge or Google Chrome.

3.  If you choose to create an app, you can choose in which environment to create it.

    ![New or existing app](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    If you choose to use an existing app, the visual prompts you to open the app in PowerApps. The visual then sets up the required components in your app so that Power BI can send data to PowerApps.

    If you create a new app, PowerApps creates a simple app with the required components already set up.

    ![New app](./media/powerapps-custom-visual/new-app.png)

4. Now in PowerApps Studio, you can use the data fields you set in step 2. The `PowerBIIntegration` object acts like any other PowerApps read-only data source or collection. You can use the object to populate any control, or join and filter with other data sources.

    ![Custom formula](./media/powerapps-custom-visual/custom-formula.png)

    This formula joins Power BI data with the Customer data source: `LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   The Power BI report and the instance of PowerApps Studio that was launched share a live data connection. While they are both open, you can filter or change the data in your report to see the updated data reflect immediately in your app in PowerApps Studio.

5. After you have completed building or making changes to your app, save and publish the app in PowerApps to see your app in the Power BI report.

6. Once you are satisfied with your changes, make sure to share the PowerApps app with users of your report and then save your report.

7. And with that, you have created a report in which your users can take actions as they gain insights from your data.

    ![Working report](./media/powerapps-custom-visual/working-report.gif)

    If you need to makes changes to an app, open the report in edit mode, click or tap **More options** (**. . .**) on the PowerApps visual and select **Edit**.

    ![Edit app](./media/powerapps-custom-visual/edit-app.png)

## Limitations of the PowerApps custom visual

The following limitations apply to the PowerApps custom visual:

- If you change the data fields associated with the visual, you must edit the app from within the Power BI service by selecting the ellipsis (...) and then selecting **Edit**. Otherwise, the changes won't be propagated to PowerApps, and the app will behave in unexpected ways.
- The PowerApps custom visual can't trigger a refresh of Power BI reports and Power BI data sources from within Power BI Desktop. If you write back data from the app to the same data source as the report, your changes won't be reflected immediately in Power BI Desktop. Changes are reflected on the next scheduled refresh.
- The PowerApps custom visual can't filter the data or send any data back to the report.
- You'll need to share the PowerApps app separately from your report. Learn about [sharing apps in PowerApps](share-app.md).
- Power BI Report Server and the mobile app for Power BI do not support the PowerApps custom visual.
- If you use PowerBIIntegration.Refresh() function, you must use a source that supports [DirectQuery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources) and the data connection must be created using DirectQuery method.
- PowerApps in Power BI Desktop provides data to PowerApps Studio when creating apps but not while editing. Use Power BI Web to preview the data while editing apps.

> [!NOTE]
> We recommend that you first publish your report to the Power BI service and then create or modify apps.

## Browser support

The following table lists the browser supportability for view, create and modify actions of the PowerApps custom visual. Supported browsers and actions are identified by a check mark ( &check; ).

|Browser|View|Create|Modify
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari|&check;
|Mozilla Firefox
|All other browsers

## Accessibility support

To navigate the PowerApps visual using the keyboard follow these steps:

1. Focus selection on the Power BI Report for the desired PowerApps visual.
2. Use the **Tab** key on the keyboard until the visual is highlighted.
3. Use the **Ctrl+Right** key on the keyboard to enter the visual.
3. Use the  **Tab** key on the keyboard until the desired component of the visual is selected.

For more information see: [Power BI Accessibility Documentation]( https://docs.microsoft.com/power-bi/desktop-accessibility)


## Next steps

* Go through a simple [step-by-step tutorial](embed-powerapps-powerbi.md).
* Check out our [video](https://aka.ms/powerappscustomvisualvideo).
