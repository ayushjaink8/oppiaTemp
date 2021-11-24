# oppiaTemp
temporary repo for oppia


I thought of doing something like this:

{{
modifyPositionValues(
    nodeData: NodeDataDict, graphWidth: number,
    graphHeight: number): NodeDataDict {
  // Change the position values in nodeData to use pixels.
  for (var nodeId in nodeData) {
    nodeData[nodeId].x0 =
      graphWidth * Number(nodeData[nodeId].x0);
    nodeData[nodeId].y0 =
      graphHeight * Number(nodeData[nodeId].y0);

    nodeData[nodeId].width =
      graphWidth * Number(nodeData[nodeId].width);
    nodeData[nodeId].height =
      graphHeight * Number(nodeData[nodeId].height);

    nodeData[nodeId].xLabel =
      graphWidth * Number(nodeData[nodeId].xLabel);
    nodeData[nodeId].yLabel =
      graphHeight * Number(nodeData[nodeId].yLabel);
  }
  return nodeData;
}

}}

Actually, what i think, the problem is.. that nodeData[nodeId] is an object (let us say: obj ).
Now, ts checks won't allow us to use obj["string"]. 

i have tried changing the NodeData interface like this:
{{{
interface NodeData {
  "depth": number;
  "offset": number;
  "reachable": boolean;
  "y0": number;
  "x0": number;
  "yLabel": number;
  "xLabel": number;
  "height": number;
  "width": number;
  "id": string;
  "label": string;
  "reachableFromEnd": boolean;
}

}}}

but this also doesn't worked for me
