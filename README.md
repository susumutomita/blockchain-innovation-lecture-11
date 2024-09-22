# blockchain-innovation-lecture-11

## Note

mv .env.example .env
mv wagmi.sample.ts wagmi.ts

modify wagmi.ts

```wagmi.ts
export const config = createConfig({
  chains: [sepolia],
  connectors: [],
  ssr: true,
  transports: {
    [sepolia.id]: http("https://eth-sepolia.g.alchemy.com/v2/<API KEY>"),
  },
});
```

modify front/wagmi-project/src/app/vote/page.tsx

```page.tsx
    writeContract(
      {
        ...TextDAOFacade,
        functionName: "voteHeaders",
        args: [args.headerIds, args.proposalId]
      },
```

modify front/wagmi-project/src/app/members/page.tsx

```page.tsx
  const {
    refetch: memberRefetch,
    data: memberData,
    isPending: isMemberPending,
  } = useReadContracts({
    contracts: [
      {
        ...TextDAOFacade,
        functionName: "getMembers",
        args: [BigInt(memberID)],
      }
    ],
  });
```
