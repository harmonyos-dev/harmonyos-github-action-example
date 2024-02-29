# HarmonyOS GitHub Action Example

- see in [CI Example](.github/workflows/ci.yml)
- see in [CD Example](.github/workflows/cd.yml)

## Know issues

### Build timeout/stuck

In GitHub Action, sometimes the build process is stuck and the job is canceled, like:

> The job running on runner GitHub Actions 3 has exceeded the maximum execution time of 360 minutes.

Log:

```
Run `npm audit` for details.

> hvigor 'npm install' executed
> hvigor Moving the SDK...
> hvigor Install task finished: ArkTS 3.2.12.5
> hvigor Finished :entry:default@PreBuild... after 194 ms 
> hvigor Finished :entry:default@GenerateMetadata... after 14 ms 
> hvigor Finished :entry:default@MergeProfile... after 4 ms 
> hvigor Finished :entry:default@BuildNativeWithCmake... after 1 ms 
> hvigor Finished :entry:default@GenerateLoaderJson... after 3 ms 
> hvigor Finished :entry:default@MakePackInfo... after 9 ms 
> hvigor Finished :entry:default@ProcessProfile... after 87 ms 
> hvigor Finished :entry:default@BuildNativeWithNinja... after 1 ms 
> hvigor Finished :entry:default@ProcessResource... after 3 ms 
> hvigor Finished :entry:default@ProcessLibs... after 5 ms 
> hvigor Finished :entry:default@CompileResource... after 187 ms 
> hvigor Finished :entry:default@CompileJS... after 4 ms 
Error: The operation was canceled.
```

Hack solution:

- add `timeout-minutes: 30` to the job, to directly cancel the job after 30 minutes

