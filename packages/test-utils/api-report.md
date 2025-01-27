## API Report File for "@backstage/test-utils"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import { AnalyticsApi } from '@backstage/core-plugin-api';
import { AnalyticsEvent } from '@backstage/core-plugin-api';
import { ApiHolder } from '@backstage/core-plugin-api';
import { ApiRef } from '@backstage/core-plugin-api';
import { AuthorizeResult } from '@backstage/plugin-permission-common';
import { ComponentType } from 'react';
import { Config } from '@backstage/config';
import { ConfigApi } from '@backstage/core-plugin-api';
import crossFetch from 'cross-fetch';
import { DiscoveryApi } from '@backstage/core-plugin-api';
import { ErrorApi } from '@backstage/core-plugin-api';
import { ErrorApiError } from '@backstage/core-plugin-api';
import { ErrorApiErrorContext } from '@backstage/core-plugin-api';
import { EvaluatePermissionRequest } from '@backstage/plugin-permission-common';
import { EvaluatePermissionResponse } from '@backstage/plugin-permission-common';
import { ExternalRouteRef } from '@backstage/core-plugin-api';
import { FetchApi } from '@backstage/core-plugin-api';
import { IdentityApi } from '@backstage/core-plugin-api';
import { JsonObject } from '@backstage/types';
import { JsonValue } from '@backstage/types';
import { Observable } from '@backstage/types';
import { PermissionApi } from '@backstage/plugin-permission-react';
import { PropsWithChildren } from 'react';
import { ReactElement } from 'react';
import { ReactNode } from 'react';
import { RenderOptions } from '@testing-library/react';
import { RenderResult } from '@testing-library/react';
import { RouteRef } from '@backstage/core-plugin-api';
import { StorageApi } from '@backstage/core-plugin-api';
import { StorageValueSnapshot } from '@backstage/core-plugin-api';

// @public
export type AsyncLogCollector = () => Promise<void>;

// @public
export type CollectedLogs<T extends LogFuncs> = {
  [key in T]: string[];
};

// @public
export function createTestAppWrapper(
  options?: TestAppOptions,
): (props: { children: ReactNode }) => JSX.Element;

// @public
export type ErrorWithContext = {
  error: ErrorApiError;
  context?: ErrorApiErrorContext;
};

// @public
export type LogCollector = AsyncLogCollector | SyncLogCollector;

// @public
export type LogFuncs = 'log' | 'warn' | 'error';

// @public
export class MockAnalyticsApi implements AnalyticsApi {
  // (undocumented)
  captureEvent(event: AnalyticsEvent): void;
  // (undocumented)
  getEvents(): AnalyticsEvent[];
}

// @public
export function mockBreakpoint(options: { matches: boolean }): void;

// @public
export class MockConfigApi implements ConfigApi {
  constructor(data: JsonObject);
  // (undocumented)
  get<T = JsonValue>(key?: string): T;
  // (undocumented)
  getBoolean(key: string): boolean;
  // (undocumented)
  getConfig(key: string): Config;
  // (undocumented)
  getConfigArray(key: string): Config[];
  // (undocumented)
  getNumber(key: string): number;
  // (undocumented)
  getOptional<T = JsonValue>(key?: string): T | undefined;
  // (undocumented)
  getOptionalBoolean(key: string): boolean | undefined;
  // (undocumented)
  getOptionalConfig(key: string): Config | undefined;
  // (undocumented)
  getOptionalConfigArray(key: string): Config[] | undefined;
  // (undocumented)
  getOptionalNumber(key: string): number | undefined;
  // (undocumented)
  getOptionalString(key: string): string | undefined;
  // (undocumented)
  getOptionalStringArray(key: string): string[] | undefined;
  // (undocumented)
  getString(key: string): string;
  // (undocumented)
  getStringArray(key: string): string[];
  // (undocumented)
  has(key: string): boolean;
  // (undocumented)
  keys(): string[];
}

// @public
export class MockErrorApi implements ErrorApi {
  constructor(options?: MockErrorApiOptions);
  // (undocumented)
  error$(): Observable<{
    error: ErrorApiError;
    context?: ErrorApiErrorContext;
  }>;
  // (undocumented)
  getErrors(): ErrorWithContext[];
  // (undocumented)
  post(error: ErrorApiError, context?: ErrorApiErrorContext): void;
  // (undocumented)
  waitForError(pattern: RegExp, timeoutMs?: number): Promise<ErrorWithContext>;
}

// @public
export type MockErrorApiOptions = {
  collect?: boolean;
};

// @public
export class MockFetchApi implements FetchApi {
  constructor(options?: MockFetchApiOptions);
  // (undocumented)
  get fetch(): typeof crossFetch;
}

// @public
export interface MockFetchApiOptions {
  baseImplementation?: undefined | 'none' | typeof crossFetch;
  injectIdentityAuth?:
    | undefined
    | {
        token: string;
      }
    | {
        identityApi: Pick<IdentityApi, 'getCredentials'>;
      };
  resolvePluginProtocol?:
    | undefined
    | {
        discoveryApi: Pick<DiscoveryApi, 'getBaseUrl'>;
      };
}

// @public
export class MockPermissionApi implements PermissionApi {
  constructor(
    requestHandler?: (
      request: EvaluatePermissionRequest,
    ) => AuthorizeResult.ALLOW | AuthorizeResult.DENY,
  );
  // (undocumented)
  authorize(
    request: EvaluatePermissionRequest,
  ): Promise<EvaluatePermissionResponse>;
}

// @alpha
export const MockPluginProvider: ({
  children,
}: PropsWithChildren<{}>) => JSX.Element;

// @public
export class MockStorageApi implements StorageApi {
  // (undocumented)
  static create(data?: MockStorageBucket): MockStorageApi;
  // (undocumented)
  forBucket(name: string): StorageApi;
  // (undocumented)
  observe$<T>(key: string): Observable<StorageValueSnapshot<T>>;
  // (undocumented)
  remove(key: string): Promise<void>;
  // (undocumented)
  set<T>(key: string, data: T): Promise<void>;
  // (undocumented)
  snapshot<T extends JsonValue>(key: string): StorageValueSnapshot<T>;
}

// @public
export type MockStorageBucket = {
  [key: string]: any;
};

// @public
export function renderInTestApp(
  Component: ComponentType | ReactNode,
  options?: TestAppOptions,
): Promise<RenderResult>;

// @public
export function renderWithEffects(
  nodes: ReactElement,
  options?: Pick<RenderOptions, 'wrapper'>,
): Promise<RenderResult>;

// @public
export function setupRequestMockHandlers(worker: {
  listen: (t: any) => void;
  close: () => void;
  resetHandlers: () => void;
}): void;

// @public
export type SyncLogCollector = () => void;

// @public
export const TestApiProvider: <T extends any[]>(
  props: TestApiProviderProps<T>,
) => JSX.Element;

// @public
export type TestApiProviderProps<TApiPairs extends any[]> = {
  apis: readonly [...TestApiProviderPropsApiPairs<TApiPairs>];
  children: ReactNode;
};

// @public
export class TestApiRegistry implements ApiHolder {
  static from<TApiPairs extends any[]>(
    ...apis: readonly [...TestApiProviderPropsApiPairs<TApiPairs>]
  ): TestApiRegistry;
  get<T>(api: ApiRef<T>): T | undefined;
}

// @public
export type TestAppOptions = {
  routeEntries?: string[];
  mountedRoutes?: {
    [path: string]: RouteRef | ExternalRouteRef;
  };
};

// @public
export function withLogCollector(
  callback: AsyncLogCollector,
): Promise<CollectedLogs<LogFuncs>>;

// @public
export function withLogCollector(
  callback: SyncLogCollector,
): CollectedLogs<LogFuncs>;

// @public
export function withLogCollector<T extends LogFuncs>(
  logsToCollect: T[],
  callback: AsyncLogCollector,
): Promise<CollectedLogs<T>>;

// @public
export function withLogCollector<T extends LogFuncs>(
  logsToCollect: T[],
  callback: SyncLogCollector,
): CollectedLogs<T>;

// @public
export function wrapInTestApp(
  Component: ComponentType | ReactNode,
  options?: TestAppOptions,
): ReactElement;
```
