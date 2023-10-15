# Fiber Middleware for charmbracelet/log

A GoFiber middleware for Charmlog logger.

- Fiber: https://github.com/gofiber/fiber
- charmbracelet/log: https://github.com/charmbracelet/log

[![tag](https://img.shields.io/github/tag/zcubbs/charmlogfiber)](https://github.com/zcubbs/charmlogfiber/releases)
![Go Version](https://img.shields.io/badge/Go-%3E%3D%201.21-%23007d9c)
[![GoDoc](https://godoc.org/github.com/zcubbs/charmlogfiber?status.svg)](https://pkg.go.dev/github.com/zcubbs/charmlogfiber)
[![Lint](https://github.com/zcubbs/charmlogfiber/actions/workflows/lint.yaml/badge.svg)](https://github.com/zcubbs/charmlogfiber/actions/workflows/lint.yaml)
[![Scan](https://github.com/zcubbs/charmlogfiber/actions/workflows/scan.yaml/badge.svg?branch=main)](https://github.com/zcubbs/charmlogfiber/actions/workflows/scan.yaml)
![Build Status](https://github.com/zcubbs/charmlogfiber/actions/workflows/test.yaml/badge.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/zcubbs/charmlogfiber)](https://goreportcard.com/report/github.com/zcubbs/charmlogfiber)
[![Contributors](https://img.shields.io/github/contributors/zcubbs/charmlogfiber)](https://github.com/zcubbs/charmlogfiber/graphs/contributors)
[![License](https://img.shields.io/github/license/zcubbs/charmlogfiber.svg)](./LICENSE)

## Usage

```go
package main

import (
    "github.com/gofiber/fiber/v2"
    "github.com/charmbracelet/log"
    "github.com/zcubbs/charmlogfiber"
    "os"
)

func main() {
    app := fiber.New()

    logger := log.New(os.Stderr)
    // Create a new logger
    fiberLogger := charmlogfiber.New(logger)

    // Use the logger in the Fiber app
    app.Use(fiberLogger)

    app.Get("/", func(c *fiber.Ctx) error {
        // Log a message
        logger.Info("Hello, World!")

        return c.SendString("Hello, World!")
    })

    app.Listen(":3000")
}
```
