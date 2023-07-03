# Simple Monorepo Expo

## Step by step

1. npx create-nx-workspace@latest <monorepo-name> --preset=ts
1. cd <monorepo-name>
1. open nx.json and modify this line:
   ```
   "workspaceLayout": {
     "appsDir": "apps",
     "libsDir": "libs"
   }
   ```
1. npm i -D @nx/expo
1. npx nx @nx/expo:app --name <app-name> --displayName "<app-display-name>"
1. cd apps/<app-name>
1. npx eas login
1. npx eas init
1. git add --all
1. git commit -m "<commit-message>"
1. npx nx run <app-name>:prebuild
1. cp tsconfig.spec.json ../melodies-e2e/
1. npx nx run <app-name>-e2e:build-android:bare
1. cd ../<app-name>-e2e
1. open .detoxrc.json and change the emulator (devices -> emulator)
1. npx nx run <app-name>-e2e:test-android:bare
