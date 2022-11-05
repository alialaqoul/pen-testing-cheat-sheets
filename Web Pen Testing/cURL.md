### cURL

Download a file:

```fundamental

curl somesite.com/somefile.txt -o somefile.txt

```

Upload a file:

```fundamental

curl somesite.com/uploads/ -T somefile.txt

```

Find out how to test a web server for various HTTP methods and method overrides from my other [project](https://github.com/ivan-sincek/forbidden).

| Option | Description |

| --- | --- |

| -d | Sends the specified data in a POST request to the HTTP server |

| -H | Extra header to include in the request when sending HTTP to a server |

| -i | Include the HTTP response headers in the output |

| -k | Proceed and operate server connections otherwise considered insecure |

| -o | Write to file instead of stdout |

| -T | Transfers the specified local file to the remote URL, same as PUT method |

| -v | Make the operation more talkative |

| -x | Use the specified proxy (\[protocol://\]host\[:port\]) |

| -X | Specifies a custom request method to use when communicating with the HTTP server |