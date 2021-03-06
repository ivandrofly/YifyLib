## NOTE
Currently working on porting to YTS.AG API (Update 2016/11/4)
* Some of the features of YTS.AG api are still under construction (i think). So going with what we have at the moment

~~_Since deprecation of API v1 by Yts, YifyLib (since v1.1) no longer support the v1 of Yts API.
See [Coming Soon](/README.md#coming-soon) section for future developments._~~

# YifyLib

## Introduction
**.NET library to access [Yts](https://yts.to/) (formaly Yify) API.**

This provide access to functionalities of [Yts API](https://yts.to/api) like,

* Searching for movies ([ListMovies](/README.md#searching-for-movies-listmovies))
* Getting movie details ([GetMovie](/README.md#getting-movie-details-getmovie))

Etc…

## Installing

You can install this library using either 

1. **[Package Manager Dialog](https://docs.nuget.org/consume/Package-Manager-Dialog)**
2. **[Package Manager Console](http://docs.nuget.org/consume/package-manager-console)** 

#### To install via Package Manager Dialog

1. Open the Package Manager Dialog.
2. Search for `YifyLib` in `Online` > `nuget.org` section.

#### To install via Package Manager Console

1. Open Package Manager Console.
2. Run the following command.

```
  Install-Package YifyLib
```

## Getting Started

#### Prerequisites

* .NET Framework 4.5 or later (Download from [here](https://www.microsoft.com/en-us/download/details.aspx?id=30653))

**_If you are planning to use more advanced features of YTS API v2 then you need:_**

* Application Key from YTS (Request one from [here](https://yts.to/contact))

#### Installing

* Install `YifyLib`

And that's it!.

---

## Examples

#### Namespaces
```c#
using YifyLib;
using YifyLib.Data;
```

#### Intialization

```c#
Yify yify = new Yify();
```
__or__
```c#
Yify yify = new Yify(new Uri("https://yts.to/api/v2/"));
```

**_If you are planning to use more advanced features of YTS API v2 then you need to initialize as:_**
```c#
Yify yify = new Yify();
yify.ApplicationKey = "<Your Application Key>";
```

#### Searching for movies (`ListMovies`)

##### Basic Search
* Search for movies where movie tile contains the word `Bourne`.
```c#
List<ListMovie> searchResult = yify.ListMovies("Bourne");
```

##### Advanced Search

* Search for movies where movie tile contains the word `Bourne`, `720p` quality and with minimum rating of 5.
```c#
List<ListMovie> result = y.ListMovies("Bourne", 
  quality: "720p", 
  minimumRating: 5);
```

###### Sorting and Ordering search result

- To Sort the search results by a particular field use `SearchResultSort` enum.
- To Order the search result in ascending or descending order use `SortOrder` enum.

Search movies where movie tile contains the word `Bourne`, sorted by added date and orderd in ascending order.
```c#
List<ListMovie> result = y.ListMovies("Bourne", 
  sortBy: SearchResultSort.DateAdded, 
  orderBy: YifyLib.SortOrder.Asc);
```

#### Getting movie details (`GetMovie`)

* Getting movie details for movie 100.

```c#
Movie m = y.GetMovie(100);
```

# Coming Soon
* YTS.AG API release (Basic Functionality)
* Changes to Examples
