# ng-forms
Form Handler for angular js

# Requirements

angular 1.6

** Note: for angular 1.5 switch to version 1.3 branch

# Usage

```javascript
var myApp = angular.module('myApp', ['ngRoute', 'ngForms']);
```

```javascript

$scope.form = {};

$scope.signin = $ngForm.create({

        url: 'login',
        method: 'post',
        scope: $scope, 
        path: 'form',
        multipart: false // optional, make it true in case of file upload

    }, {

        success: function (o) {

        }

    });
    

```

```html
  <form class="login-form">
      <h1>Login to your account</h1>

      <div  uib-alert  close="dismiss()"  ng-hide="form.response.alert.class == undefined" class="alert alert-{{form.response.alert.class}}">{{form.response.alert.text}}</div>
        
      <div class="form-group" ng-class="{'has-error': form.response.hasError('email')}">
              <label for="inputEmail" class="sr-only">Username or Email</label>
              <input  ng-model="form.username" type="text" id="inputEmail" class="form-control" placeholder="Username or Email" required autofocus>
              <div class="help-block">{{form.response.error('email')}}</div>
      </div>
      
      <div class="form-group" ng-class="{'has-error': form.response.hasError('email')}">
              <label for="inputPassword" class="sr-only">Password</label>
              <input  ng-model="form.password" type="password" id="inputPassword" class="form-control" placeholder="Password" required>
              <div class="help-block">{{form.response.error('email')}}</div>
      <div>
      <div class="checkbox">
        <label>
          <input type="checkbox" value="remember-me" ng-model="form.remember"> Remember me
        </label>
      </div>
      <button class="btn btn-primary btn-block" type="submit"  ng-click="signin.handle()">Sign in</button>
    </form>
```

**ng-forms is built especially for laravel developers**

```php

// Laravel validations
$validation = Validator::make($request->all(), $rules);

if ($validation->fails()) {
	return ['success' => false, 'errors' => $validation->errors()];
}
```

**Note: dismiss function will hide alert. directly bind to some button or use in angular-ui close attribute**

**Ver:1.2**
- 2 functions added for error handling (hasError() and error() in server response object)
