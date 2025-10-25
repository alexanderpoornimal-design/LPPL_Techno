# [LankaPay Dashboard](https://lankapay.com/dashboard) [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social&logo=twitter)](https://twitter.com/intent/tweet?url=https://lankapay.com/dashboard&text=Check%20LankaPay%20Dashboard%20#webdesign%20#dashboard%20#antdesign%20#vue%20#payments%20https://lankapay.com/dashboard)

![version](https://img.shields.io/badge/version-1.0.0-blue.svg) [![GitHub issues open](https://img.shields.io/github/issues/lankapay/dashboard.svg)](https://github.com/lankapay/dashboard/issues?q=is%3Aopen+is%3Aissue) [![GitHub issues closed](https://img.shields.io/github/issues-closed-raw/lankapay/dashboard.svg)](https://github.com/lankapay/dashboard/issues?q=is%3Aissue+is%3Aclosed)

![Image](https://s3.amazonaws.com/creativetim_bucket/products/494/original/opt_md_ant_thumbnail.jpg)

LankaPay Dashboard is a comprehensive payment management dashboard built with Vue.js and Ant Design, designed for modern payment processing and financial management.

Designed for payment service providers, fintech companies, and financial institutions. Made with modern UI components and fully responsive design, LankaPay Dashboard is ready to help you manage payments, transactions, and financial data.

We created many examples for pages like Payment Processing, Transaction Management, Merchant Management and so on. Just choose between different payment flows and you are good to go!

**Fully Coded Elements**

LankaPay Dashboard is built with over 70 frontend individual elements, like buttons, inputs, navbars, navtabs, cards or alerts, giving you the freedom of choosing and combining. All components can take variations in colour, that you can easily modify using SASS files and classes. You will save a lot of time going from prototyping to full-functional code, because all elements are implemented.

View <a href="https://lankapay.com/docs" target="_blank">all components here</a>.

**Documentation built by Developers**

Each element is well presented in a very complex documentation.
You can read more about the <a href="https://lankapay.com/docs" target="_blank">documentation here</a>.

**Example Pages**

If you want to get inspiration or just show something directly to your clients,
you can jump start your development with our pre-built example pages. You will be able
to quickly set up the basic structure for your payment management system.
View <a href="https://lankapay.com/dashboard" target="_blank">example pages here</a>.

**HELPFUL LINKS**

- View <a href="https://github.com/lankapay/dashboard" target="_blank">Github Repository</a>

- Check <a href="https://lankapay.com/faq" target="_blank">FAQ Page</a>

**Special thanks**

During the development of this dashboard, we have used many existing resources from awesome developers. We want to thank them for providing their tools open source:

- [Ant Design Vue](https://www.antdv.com/docs/vue/introduce/)- An enterprise-class UI design language for web applications

Let us know your thoughts below. And good luck with development!

## Table of Contents

* [Versions](#versions)
* [Demo](#demo)
* [Quick Start](#quick-start)
* [Deploy](#deploy)
* [Documentation](#documentation)
* [File Structure](#file-structure)
* [Browser Support](#browser-support)
* [Resources](#resources)
* [Reporting Issues](#reporting-issues)
* [Technical Support or Questions](#technical-support-or-questions)
* [Licensing](#licensing)
* [Useful Links](#useful-links)

## Versions

[<img src="https://s3.amazonaws.com/creativetim_bucket/github/html.png" width="60" height="60" />](https://www.creative-tim.com/product/muse-vue-ant-design-dashboard?ref=readme-sud)

| HTML |
| --- |
| [![Muse Vue Ant Design Dashboard](https://s3.amazonaws.com/creativetim_bucket/products/494/thumb/opt_md_ant_thumbnail.jpg)](http://demos.creative-tim.com/muse-vue-ant-design-dashboard?ref=readme-sud)

## Demo

- [Dashboard page](https://lankapay.com/dashboard)
- [Sign in page](https://lankapay.com/sign-in)
- [Sign up page](https://lankapay.com/sign-up)

[View More](https://lankapay.com/dashboard).

## Quick start

Quick start options:

- Download from [LankaPay](https://lankapay.com/dashboard).

## Terminal Commands

1. Download and Install NodeJs from [NodeJs Official Page](https://nodejs.org/en/download/).
2. Navigate to the root / directory and run npm install to install our local dependencies.

## Deploy

:rocket: You can deploy your own version of the LankaPay Dashboard to Genezio with one click:

[![Deploy to Genezio](https://raw.githubusercontent.com/Genez-io/graphics/main/svg/deploy-button.svg)](https://app.genez.io/start/deploy?repository=https://github.com/lankapay/dashboard&utm_source=github&utm_medium=referral&utm_campaign=github-lankapay&utm_term=deploy-project&utm_content=button-head)

## Documentation
The documentation for the LankaPay Dashboard is hosted at our [website](https://lankapay.com/docs).

### What's included

Within the download you'll find the following directories and files:

```
lankapay-dashboard
├── LICENSE
├── README.md
├── babel.config.js
├── gulpfile.js
├── package.json
├── public
│   ├── imagesd
│   └── index.html
├── src
│   ├── App.vue
│   ├── assets
│   ├── components
│   │   ├── Cards
│   │   │   ├── CardAuthorTable.vue
│   │   │   ├── CardBarChart.vue
│   │   │   ├── CardBillingInfo.vue
│   │   │   ├── CardConversations.vue
│   │   │   ├── CardCredit.vue
│   │   │   ├── CardInfo.vue
│   │   │   ├── CardInfo2.vue
│   │   │   ├── CardInvoices.vue
│   │   │   ├── CardLineChart.vue
│   │   │   ├── CardOrderHistory.vue
│   │   │   ├── CardPaymentMethods.vue
│   │   │   ├── CardPlatformSettings.vue
│   │   │   ├── CardProfileInformation.vue
│   │   │   ├── CardProject.vue
│   │   │   ├── CardProjectTable.vue
│   │   │   ├── CardProjectTable2.vue
│   │   │   └── CardTransactions.vue
│   │   ├── Charts
│   │   │   ├── ChartBar.vue
│   │   │   └── ChartLine.vue
│   │   ├── Footers
│   │   │   ├── DashboardFooter.vue
│   │   │   └── DefaultFooter.vue
│   │   ├── Headers
│   │   │   ├── DashboardHeader.vue
│   │   │   └── DefaultHeader.vue
│   │   ├── Sidebars
│   │   │   ├── DashboardSettingsDrawer.vue
│   │   │   └── DashboardSidebar.vue
│   │   └── Widgets
│   │       ├── WidgetCounter.vue
│   │       └── WidgetSalary.vue
│   ├── layouts
│   │   ├── Dashboard.vue
│   │   ├── DashboardRTL.vue
│   │   └── Default.vue
│   ├── main.js
│   ├── plugins
│   │   └── click-away.js
│   ├── router
│   │   └── index.js
│   ├── scss
│   │   ├── app.scss
│   │   ├── base
│   │   │   ├── _override.scss
│   │   │   ├── _typography.scss
│   │   │   ├── _utilities.scss
│   │   │   └── _variables.scss
│   │   ├── components
│   │   │   ├── _avatar.scss
│   │   │   ├── _badge.scss
│   │   │   ├── _button.scss
│   │   │   ├── _card.scss
│   │   │   ├── _chart.scss
│   │   │   ├── _dropdown.scss
│   │   │   ├── _list.scss
│   │   │   ├── _progress.scss
│   │   │   ├── _settings-drawer.scss
│   │   │   ├── _space.scss
│   │   │   ├── _table.scss
│   │   │   ├── _tag.scss
│   │   │   ├── _timeline.scss
│   │   │   └── _widget.scss
│   │   ├── form
│   │   │   ├── _checkbox.scss
│   │   │   └── _input.scss
│   │   ├── layouts
│   │   │   ├── _dashboard-rtl.scss
│   │   │   ├── _dashboard.scss
│   │   │   └── _default.scss
│   │   └── pages
│   │       ├── _profile.scss
│   │       ├── _sign-in.scss
│   │       └── _sign-up.scss
│   └── views
│       ├── 404.vue
│       ├── Billing.vue
│       ├── Dashboard.vue
│       ├── Layout.vue
│       ├── Profile.vue
│       ├── RTL.vue
│       ├── Sign-In.vue
│       ├── Sign-Up.vue
│       └── Tables.vue
└── vue.config.js
```

## Browser Support

At present, we officially aim to support the last two versions of the following browsers:

<img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/chrome.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/firefox.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/edge.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/safari.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/opera.png" width="64" height="64">

## Resources
- [Live Preview](https://lankapay.com/dashboard)
- [Download Page](https://lankapay.com/dashboard)
- Documentation is [here](https://lankapay.com/docs)
- [License Agreement](https://lankapay.com/license)
- [Support](https://lankapay.com/contact)
- Issues: [Github Issues Page](https://github.com/lankapay/dashboard/issues)

## Reporting Issues
We use GitHub Issues as the official bug tracker for the LankaPay Dashboard. Here are some advices for our users that want to report an issue:

1. Make sure that you are using the latest version of the LankaPay Dashboard. Check the CHANGELOG from your dashboard on our [website](https://lankapay.com/dashboard).
2. Providing us reproducible steps for the issue will shorten the time it takes for it to be fixed.
3. Some issues may be browser specific, so specifying in what browser you encountered the issue might help.

## Technical Support or Questions

If you have questions or need help integrating the product please [contact us](https://lankapay.com/contact) instead of opening an issue.

## Licensing

- Copyright 2024 [LankaPay](https://lankapay.com)
- LankaPay [license](https://lankapay.com/license)

## Useful Links

- [More products](https://lankapay.com/products) from LankaPay

- [Tutorials](https://lankapay.com/tutorials)

- [API Documentation](https://lankapay.com/api-docs)

- [Developer Resources](https://lankapay.com/developers)

##### Social Media

Twitter: <https://twitter.com/LankaPay>

Facebook: <https://www.facebook.com/LankaPay>

LinkedIn: <https://linkedin.com/company/lankapay>

Instagram: <https://instagram.com/lankapay>
