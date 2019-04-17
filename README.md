# nuxt-scss-starter

## Add global scss files
* add scss files to assets/scss directory or such as your favorite direcotry. Then update nuxt.config.json to add the path.

```json
  styleResources: {
    scss: [
      '~/assets/scss/_base.scss',
      '~/path/to/{your_style}.scss',
    ]
  },
```

* Reboot 