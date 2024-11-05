# Menu custom icon / logo

## Default.xml
`app/code/CreationLabs/Admin/view/adminhtml/layout/default.xml`

```xml
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <head>
        <css src="CreationLabs_Admin::css/style.css"/>
    </head>
</page>
```

## style.css

`app/code/CreationLabs/Admin/view/adminhtml/web/css/style.css`

```css
#menu-creationlabs-top-level > a:before {
    content: "";
    height: 39px;
    margin: 0 auto;
    width: 78px;
    background: url('../images/logo.svg') no-repeat;
    background-size: contain;
    background-position-y: center;
}

#menu-creationlabs-top-level > a > span {
    display: none;
}
```

## Icon
`app/code/CreationLabs/Admin/view/adminhtml/web/images/logo.svg`

```svg
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="152" height="26" viewBox="0 0 152 26"><defs><path id="f4q9b" d="M75 45.831h6.578v-6.59H75z"/><path id="f4q9c" d="M81.58 45.832h6.578v-6.59H81.58z"/><path id="f4q9d" d="M113.387 48.735c-1.938 1.907-3.978 2.656-6.459 2.656-4.86 0-8.906-2.929-8.906-8.888 0-5.96 4.046-8.889 8.906-8.889 2.38 0 4.216.68 6.052 2.487l-2.619 2.758c-.986-.886-2.208-1.328-3.365-1.328-2.786 0-4.827 2.044-4.827 4.972 0 3.2 2.175 4.903 4.76 4.903 1.325 0 2.652-.374 3.67-1.396z"/><path id="f4q9e" d="M119.066 34.085l.306 1.94c1.292-2.076 3.026-2.383 4.726-2.383 1.733 0 3.399.68 4.316 1.601l-1.87 3.61c-.85-.716-1.631-1.09-2.99-1.09-2.176 0-4.182 1.157-4.182 4.258v8.854h-4.148v-16.79z"/><path id="f4q9f" d="M133.512 43.964c.272 2.077 2.073 3.577 4.997 3.577 1.53 0 3.534-.58 4.487-1.568l2.652 2.622c-1.769 1.84-4.658 2.725-7.208 2.725-5.778 0-9.211-3.576-9.211-8.957 0-5.108 3.467-8.786 8.906-8.786 5.608 0 9.11 3.474 8.463 10.387zm9.11-3.44c-.273-2.179-1.972-3.269-4.351-3.269-2.244 0-4.08 1.09-4.692 3.27z"/><path id="f4q9g" d="M163.086 34.089h3.977v16.79h-3.909l-.203-2.453c-.951 1.975-3.57 2.928-5.44 2.962-4.962.036-8.633-3.03-8.633-8.921 0-5.79 3.841-8.82 8.736-8.787 2.244 0 4.386 1.056 5.337 2.725zm-10.06 8.373c0 3.198 2.207 5.103 4.957 5.103 6.52 0 6.52-10.173 0-10.173-2.75 0-4.958 1.871-4.958 5.07z"/><path id="f4q9h" d="M170.491 34.12v-3.264l4.148-1.504v4.767h4.622v3.576h-4.657v7.254c0 1.601.885 2.384 2.175 2.384.647 0 1.395-.204 2.005-.51l1.156 3.54c-1.189.478-2.174.682-3.433.717-3.637.136-6.016-1.942-6.016-6.13v-7.255"/><path id="f4q9a" d="M75 51.389h151.608v-24.46H75z"/><path id="f4q9j" d="M186.87 29.355c0 3.235-4.895 3.235-4.895 0s4.894-3.235 4.894 0zm-4.523 21.523h4.157V34.021h-4.157z"/><path id="f4q9k" d="M207.261 42.497c0 4.835-3.296 8.75-8.734 8.75-5.44 0-8.702-3.915-8.702-8.75 0-4.803 3.33-8.753 8.668-8.753 5.336 0 8.768 3.95 8.768 8.753m-13.29 0c0 2.554 1.53 4.936 4.556 4.936 3.024 0 4.554-2.382 4.554-4.936 0-2.521-1.767-4.973-4.554-4.973-2.993 0-4.556 2.452-4.556 4.973"/><path id="f4q9l" d="M222.46 50.881v-8.787c0-2.554-1.393-4.495-4.043-4.495-2.55 0-4.283 2.146-4.283 4.7v8.582h-4.114V34.057h3.705l.272 2.283c1.7-1.67 3.4-2.521 5.508-2.521 3.942 0 7.103 2.963 7.103 8.24v8.822z"/><clipPath id="f4q9i"><use xlink:href="#f4q9a"/></clipPath></defs><g><g transform="translate(-75 -26)"><g><g><use fill="#dc352f" xlink:href="#f4q9b"/></g><g><use fill="#b7b9bc" xlink:href="#f4q9c"/></g><g><g><use fill="#fff" xlink:href="#f4q9d"/></g><g><use fill="#fff" xlink:href="#f4q9e"/></g><g><use fill="#fff" xlink:href="#f4q9f"/></g><g><use fill="#fff" xlink:href="#f4q9g"/></g><g><use fill="#fff" xlink:href="#f4q9h"/></g><g/><g clip-path="url(#f4q9i)"><use fill="#fff" xlink:href="#f4q9j"/></g><g clip-path="url(#f4q9i)"><use fill="#fff" xlink:href="#f4q9k"/></g><g clip-path="url(#f4q9i)"><use fill="#fff" xlink:href="#f4q9l"/></g></g></g></g></g></svg>
```