# Enzyme and Jest expect helpers
Simple expect helpers for unit testing with Jest and Enzyme

## Usage examples

```jsx
import React from 'react';
import { shallow, mount } from 'enzyme';
import {
  expectComponentToBe,
  expectComponentToHaveChildren,
  expectComponentToHaveProps,
  expectComponentToHaveDisplayName,
  } from '@lodgify/enzyme-jest-expect-helpers';
import { Button as LodgifyButton } from '@lodgify/ui';

import { PrimaryButton } from './PrimaryButton';

const getButton = props => shallow(<Button {...props}>Press me</Button>);

describe('<PrimaryButton />', () => {
  it('should render a single `LodgifyButton` component', () => {
    const wrapper = getButton();
    expectComponentToBe(wrapper, LodgifyButton);
  });

  it('should have the the right props', () => {
    const wrapper = getButton();
    expectComponentToHaveProps(wrapper, {
      isLoading: false,
      isRounded: true,
    });
  });

  it('should render the right children', () => {
    const wrapper = getButton();
    expectComponentToHaveChildren(wrapper, 'Press me');
  });

  it('should have `displayName` PrimaryButton', () => {
    expectComponentToHaveDisplayName(PrimaryButton, 'PrimaryButton')
  });
});
```
