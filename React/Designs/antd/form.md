# Forms
## Setup
1. Import **Form** from  ant Design library
2. Get form item as **Form.item**
3. Wrap your component in **form.create()(App)**

## Basic Example
```jsx
import React from 'react';
import { Form, Input, Button } from 'antd';
const FormItem = Form.Item;

const App = props => {
  handleSubmit = e => {
    e.preventDefault();
    this.props.validateFields((err, values) => {
      if (!err) {
        // do somethign with values
        // values.heading will have value given in form 
      }
    });
  };
  const { getFieldDecorator } = this.props;
  return (
    <Form onSubmit={handleSubmit}>
      <FormItem label="heading">
        {getFieldDecorator('variable name', {
          rules: [
            { 
              required: true, 
              message: 'Please input your name'
            }
          ]
        })(<Input />)}
      </FormItem>
    </Form>
  );
};

export default Form.create()(App);
```

## Rules
These are the rules you can give

---

**NOTE**:
all of these can be supported by a message

---

| property   | description                                           | value                                           |
| ---------- | ----------------------------------------------------- | ----------------------------------------------- |
| length     | the exact length the form item can have               | number                                          |
| min        | the min length the form item can have                 | number                                          |
| max        | the max length the form item can have                 | number                                          |
| pattern    | validate from a regular expression                    | RegExp                                          |
| required   | indicates whether field is required                   | boolean                                         |
| transform  | transform a value before validation                   | function(value) return newvalue                 |
| type       | set a type for the field                              | can take one the string values                  |
| validator  | custom validate function                              | function(rule, value, callback) return newvalue |
| whitespace | if true, in required fields, only whitespace = errors | boolean                                         |

---

**NOTE**:
we can make this using only FormItem and its props **help**(shows a message), **validateStatus**(takes a function that must return an object with 2 properties, **validateStatus** and **errorMsg**, set to null in case of success)

---

## Creating form parameters
