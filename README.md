# Personal local Julia registry

This project is a lightweight Julia registry for personal and third-party Git-hosted Julia packages. I use it to ensure replicability and consistent versioning between interdependent packages that are not ready to be uploaded to Julia's General registry yet. It is managed using the [LocalRegistry.jl](https://github.com/GunnarFarneback/LocalRegistry.jl) package.

## Adding this registry to your local machine

To add this registry to your local machine -- e.g. because you are working with one of my packages that depends on a package in this registry -- you simply need to run

```julia
julia> Pkg.Registry.add(RegistrySpec(url="git@github.com:joschakrug/LocalJuliaRepo.git"))
```

once in your local Julia REPL. From this moment on, you will be able to `] add` or `] update` any packages listed in it just as you would be able to add an official Julia package.

## Adding packages to this registry or updating them

If you have writing rights to this GitHub repository, adding or updating packages to this registry is straightforward. First, make sure that you have added the registry on your local machine as described above.

Then, to **either add or update** a package, make sure that you have pushed a version-tagged commit with the corresponding version number in the project's `Project.toml` to the project's Git repository. Once that is done, simply run

```julia
julia> using LocalRegistry
julia> register("path/to/NewPackageRepo", registry = "LocalJuliaRepo", push = true)
```
